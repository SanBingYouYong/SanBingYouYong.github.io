# A Decay Function for Exploration-Exploitation Handling in Reinforcement Learning

In the context of reinforment learning, we wish to set up a e-greedy policy to allow for some exploration at the start, and exponential decay of e meets the Greedy-in-the-Limit & Infinite Exploration requirement for exploratory methods.

In practice, we often find the need to precisely define when does the major exploratory period ends and by what threshold, to put it in another way, we want to let e to decay to a threshold `a` after `b` time steps.

A usual exponential decay functions takes the form: <math xmlns="http://www.w3.org/1998/Math/MathML">
  <mi>ε</mi>
  <mo>=</mo>
  <msup>
    <mi>e</mi>
    <mrow>
      <mo>-</mo>
      <mi>k</mi>
      <mi>t</mi>
    </mrow>
  </msup>
</math> where `k` is a constant controling the decay and `t` is the current time step. We carry out some manual experiment and find out: <math xmlns="http://www.w3.org/1998/Math/MathML">
  <mi>ε</mi>
  <mo>=</mo>
  <msup>
    <mi>e</mi>
    <mrow>
      <mo>-</mo>
      <mfrac>
        <mn>1</mn>
        <mrow>
          <mn>3</mn>
          <mi>a</mi>
          <mi>b</mi>
        </mrow>
      </mfrac>
      <mi>t</mi>
    </mrow>
  </msup>
</math> apprxoimates our requirements. We generalize this form to find an exact solution for some constant that replaces 1/3: <math xmlns="http://www.w3.org/1998/Math/MathML">
  <mi>ε</mi>
  <mo>=</mo>
  <msup>
    <mi>e</mi>
    <mrow>
      <mo>-</mo>
      <mfrac>
        <mi>c</mi>
        <mrow>
          <mi>a</mi>
          <mi>b</mi>
        </mrow>
      </mfrac>
      <mi>t</mi>
    </mrow>
  </msup>
</math>.

Solving for the above equation =a yields `c=-a*ln(a)`, and inserting it back we end up with <math xmlns="http://www.w3.org/1998/Math/MathML">
  <mi>ε</mi>
  <mo>=</mo>
  <msup>
    <mi>e</mi>
    <mrow>
      <mfrac>
        <mrow>
          <mo>ln</mo>
          <mi>a</mi>
        </mrow>
        <mi>b</mi>
      </mfrac>
      <mi>t</mi>
    </mrow>
  </msup>
</math>, where `a` is the decay target (e.g. 0.1) at time step `b` (e.g. after 50 steps), and `t` the time step. Note that we removed the `k` parameter to control the decay since even if we added it, it's gonna cancel itself out - makes sense intuitively if we already control the decay with a set point `(b, a)`. However, it is possible to define a more complex or a piece-wise decay function that allows control over decay speed before (and/or) after the thresholding point.

![a](./figs/decay_function_1.svg)
![b](./figs/decay_function_2.svg)
Blue line is the decay function, with red and orange lines' intersection showing `(b, a)`

To check it on [desmos](https://www.desmos.com/calculator/mzq8mrjyj3).
