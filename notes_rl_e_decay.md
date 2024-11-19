# A Decay Function for Exploration-Exploitation Handling in Reinforcement Learning

In the context of reinforcement learning, we wish to set up an \(\epsilon\)-greedy policy to allow for some exploration at the start, and exponential decay of \(\epsilon\) meets the Greedy-in-the-Limit & Infinite Exploration requirement for exploratory methods.

In practice, we often need to precisely define when the major exploratory period ends and by what threshold. To put it another way, we want \(\epsilon\) to decay to a threshold \(a\) after \(b\) time steps.

A usual exponential decay function takes the form \(\epsilon = e^{-kt}\), where \(k\) is a constant controlling the decay and \(t\) is the current time step. Through some manual experimentation, we find that \(\epsilon = e^{-\frac{1}{3ab}t}\) approximates our requirements. We generalize this form to find an exact solution by replacing the \(\frac{1}{3}\) constant: \(\epsilon = e^{-\frac{c}{ab}t}\).

Solving for \(e^{-\frac{c}{ab}t} = a\) yields \(c = -a \ln a\). Plugging this back, we end up with:

\[
\epsilon = e^{\frac{\ln a}{b}t}
\]

where:

- \(a\) is the decay target (e.g., 0.1) at time step \(b\) (e.g., after 50 steps).
- \(t\) is the current time step.

Note that we removed the \(k\) parameter used to control the decay since adding it would cancel out. This makes sense intuitively because we already control the decay with a set point \((b, a)\). However, it is possible to define a more complex or piecewise decay function to adjust the decay speed before and/or after the threshold point.

![a](./figs/decay_function_1.svg)
![b](./figs/decay_function_2.svg)
Blue line is the decay function, with red and orange lines' intersection showing (b, a)

To check it on [desmos](https://www.desmos.com/calculator/mzq8mrjyj3).
