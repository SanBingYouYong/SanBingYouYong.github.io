# Resume
ZHANG Shuyuan - [email](rayzhang707@gmail.com) - [website](sanbingyouyong.github.io)

## Education
- The University of Edinburgh (2020 ~ 2024)
    - BSc Computer Science (Honours)
    - Weighted average grade: 78 (First Class)
- Imperial College London (2024 ~ 2025)
    - MSc Advanced Computing

## Highlights
### Computer Vision / Computer Graphics
- UoE Course: *Computer Graphics: Rendering* & *Computer Graphics: Geometry and Simulation*
    - Learn C++ from scratch and implement **Ray Tracing** with advanced features including texture, acceleration hierarchy based on BVH, path tracing, pixel sampling, lens/aperture sampling and light sampling
    - **Mesh Reconstruction** from point clouds, discrete analysis and parameterization
- UoE Bachelor Dissertation: *Inverse Procedural Modeling: from Sketches to Buildings*
    - Construct a procedural model for buildings based on Directed Acyclic Graphs (DAG)
    - Distort 3D models and render as a 2D sketch image; generate training data with parameter sampling
    - Encoder-decoder & Multi-task decoders that predict DAG parameters based on input sketch image
    - Develop Blender add-on as user interface

### Natural Language Processing
- UoE Coursess: *Foundations of Natural Language Processing* & *Natural Language Understanding, Generation and Machine Translation*
    - N-gram, Bayesian probabilities, RNN, GRU, LSTM, Transformer and Attention mechanism
    - Group Project for the course *Machine Learning Practical*: Query-focused Summarization via GPT Prompting on Ambiguous QA
- Extracurricular Application: 
    - N-gram probabilities from Chinese poetry and as a name-generator mod for the game Stellaris, with over 500 subscriptions. 

### Large Language Models
- Application: 
    - Prompt Engineering, Multi-agent systems, OpenAI API, Ollama API
    - Task breakdown for better performance and robustness via designing and implementing Multi-agent systems
    - Generate fine-tune data for low-resource tasks
    - Deployed on remote server [QAnything](https://github.com/netease-youdao/QAnything) to serve as a LLM backend with knowledge base

### Digital Humans
- Deployed on remote server, extended and contributed to the open-source metahuman framework [Linly_Talker](https://github.com/Kedreamix/Linly-Talker), working with QAnything as an extra method to generate speech text for digital humans
- Deployed on remote server [GPT-SoVITS](https://github.com/RVC-Boss/GPT-SoVITS) to fine-tune models for voice cloning
- Deployed on remote server [metahuman-stream](https://github.com/lipku/metahuman-stream) as a real-time digital human streaming method

### Internet of Things
- UoE Course: *Principles and Design of IoT Systems*
    - Collect human activity data through wearable devices
    - Design, implement and train neural networks (CNN, RNN, LSTM with model ensembling) to identify activity and respiratory symptoms
    - Develop Android App to deploy trained models, connect to sensors via Bluetooth and classify human activities /respiratory symptoms in real-time

### System Engineering
- Group Project: A domino-placing robot based on TurtleBot, Lego motors, 3D printed parts and an Android App for Bluetooth connection to the robot for the course *System Design Project*
    - Designed the domino-reloading and automatic placement mechanism
    - Designed and modelled the 3D printed parts
    - Wrote Python scripts to control the Lego motors
    - Coordinated Android App development
    - Designed and implemented the communication method between server, robot and the app


## Work Experience
- HGTech - R&D Intern (Summer 2024)
    - Worked on digital human topics, deployed various services on compute server directly or using docker containers, hosted locally a Streamlit-driven webpage to track service status
- VisionTalk - Algorithms Intern (June 2024)
    - Improved LLM performance and robustness on chat generation and decision making via breaking down a complex task and designing/implementing a Multi-agent system
- GraphviX Lab, IPAB, UoE - Summer Research Internship (Summer 2023)
    - Researched on topics of sketch-based inverse procedural modeling. Implemented shape grammars based on Blender geometry nodes and its APIs. Trained neural networks to inference shape parameters from sketches, and integrated above pipelines as a Blender plug-in. Some tech stacks are also part of my bachelor dissertation. 
- UoE - Tutor (2023)
    - A paid position delivering weekly tutorials for the course *Reasoning and Agents*, two hours per week
- EUFS - Software Infrastructure (2022 ~ 2023/24)
    - Software Infrastructure team for Driverless Vehicle
        - Maintained, refactored and extended `eufs_cli`, the command-line-interface tool in Python
            - refactored 70 lines of repeated code for each command to 5 lines
        - Provide supporting functionalities around git, colcon and more
        - Contributed to the server backend of EUFS-Testing-Application
        - Update launch configurations of the self-driving race car under different tasks
- Wuhan Tianyu Information Industry - Algorithms Intern (Summer 2021)
    - Carried out object detection tasks using OpenCV-Python and YOLOv5, trained models focusing on human and traffic analysis tasks. Wrote scripts to process large amount ofArUco codes. Collected, cleaned and augmented dataset for training
