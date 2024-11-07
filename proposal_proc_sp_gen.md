# A Proposal: Neural Generation of Novel Procedural Shape Programs from 3D Mesh Data
September 2024

## Motivation
Procedural modeling is a powerful tool for generating complex 3D shapes through manipulating a limited number of parameters, yet creating the procedural programs is a challenging task. There exists various work in the Inverse Procedural Modeling domain that rely on existing shape programs to achieve automatic inference on shape parameters, however, few work had focused on solving the problem of generating novel shape programs from scratch. 

The furthest goal for such a field of study can be abstracted as follows: given user requests in arbitrary form, an ideal solution should be able to generate a procedural program that can produce the desired 3D shape, at the same time exposing parameters that are easy to manipulate for the user.

We may consider a gradual process of decomposing the grand goal into smaller, more manageable sub-tasks as the following: 
- starting with accepting user requests as **text prompts**, one problem is the lack of detailed information on the desired shape - "generate a chair" provides only the domain information, as an example of a bad prompt. This is where LLMs may get involved, for example in filling in details to the prompt; 
- we take the first step back, from accepting text prompts to accepting **2D images** provided by the user, either sketch images or photo-realistic ones - this task is backed up by sufficient details from images directly, and various techniques like differentiable rendering can help in ensuring that the generated shape matches user request. We may also step back to text prompts utilizing text-to-image models. 
- we then take the second step back, now accepting **3D mesh** data as inputs directly - similarly, this step can be taken forward again with existing image-based 3D shape retrieval/reconstruction methods, and we now have access to more direct information on what the user wishes to generate. Optimization techniques would be helpful in constraining the generative model, however, we must stay aware that although optimization pipelines may yield better results, it is not easy to replace the mesh-based optimization method with similar module available in 2D or for text. Therefore, we should aim for single-pass synthesis method in this step. 
- Besides these two steps, we may find another semi-isolated problem: there exists a trade-off between the **expressiveness** of the program and the **ease of manipulation** for the user, and with current Inverse Procedural Modeling methods, the above grand goal can be simplified: with an **automatic parameter-filling** model, our generated procedural program does not need to be easy to interpret or necessarily manipulated by human users. 
Or see this figure: 
![steps](./figs/steps.pdf) TODO png

This proposal attempts to tackle the second step back mentioned above, which is generating novel procedural shape programs from 3D mesh data. 


## Method Overview
The proposed method has a straight-forward inference process (visualized in the below figure): given a 3D mesh as input, we employ a state-of-the-art mesh encoder to produce a feature embedding, and a text-generation decoder network trained on gathered data will produce a shape program as executable program code that can reproduce the input mesh, finally with proper refactoring, we end up with a new procedural shape program that include the original input mesh as one of its output variations. 

![inference](./figs/inference.pdf) TODO png

In terms of data preparation and training, we take high level inspiration from the work on diffusion models from *diffusion*, which creates training data through disturbing an original piece of data entry. As visualized in following figure, given an arbitrary procedural shape program, we create disturbed training data in two ways: 
![data_prep_and_training](./figs/data_prep_and_training.pdf) TODO png

- we sample the parameters of the procedural program, and we embed the parameter values into the shape program to end up with a new data entry (namely, a procedural shape program with parameter values embedded inside); 
- we randomly disturb the procedural program itself, in ways such as changing hard-coded values, removing / switching code blocks and tweaking statement in the code; now we receive a set of new shape programs, which, their outputs may not be meaningful or related to the original shape domain anymore, however, this is intended since we expect the decoder to learn to generate arbitrary shapes. This step can also be done with prompting LLMs, and early experiments already yielded satisfactory results as shown in the following figure. A simple LLM-based perturb algorithm is summarized in the next figure too. 

![perturbs](./figs/perturbs.pdf) TODO png
![perturb_alg](./figs/perturb_alg.pdf) TODO png

The rest of the data preparation and training process is also visualized already: we execute the shape programs in shape engine to obtain corresponding mesh, and we encode them with the same mesh encoder we will use in inference to obtain mesh embeddings. Pairing the generated feature embedding and the shape program, we now have a dataset for training the decoder network. 

Note that properly exposed parameters are a necessary part of a procedural model, thus, in the first step above we may record a new set of data (of shape programs with exposed parameters and corresponding programs with embedded parameter values) for training a Shape Program Refactoring model, which in its essence will be another decoder model. 

## Other Thoughts
The lack of optimization in the process yields its own pros and cons: it is now easy to migrate the how pipeline to 2D image data as input, but there is chance that we cannot explicitly control the quality of generated shape programs. This can serve as a fallback option, in case the performance of the single-pass decoder network suffers, and when migrating to 2D, as mentioned previously, there are work-arounds for 3D mesh-based constraints. In fact, in the earliest versions of this proposal, a purely text-based and prompting-based solution with visual LMs was involved, but with the risk of a never-converging optimization loop. This proposal is thus open to more discussions. 

