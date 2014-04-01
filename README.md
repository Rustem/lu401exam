lu401exam
=========

# Table of Contents

1. [Channel capacity calculation](#channel-capacity-calculation)
2. [Pulse code modulation](#pulse-code-modulation)
3. [Matched filter](#matched-filter)
4. [Adaptive quantiser](#adaptive-quantiser)
5. [ASK modulation](#ask-modulation)
6. [Common scheme](#common-scheme)

# Adaptive quantiser
Quantiser approximates a continuous signal `x(t)` with a discrete signal `xQ(t)` in order to get a smaller set of input values. It is also an essential aspect of analogue-to-digital conversion.

Quantisation > Scalar > Adaptive (Forward "AQF" and Backward "AQB").

__Scalar quantisation__ is the most common type of quantisation and can be as simple as rounding high-precision numbers to the nearest integers.

The adaptation concept of varying the quantisation (staircase) characteristic with time and in harmony to the local statistics of the input speech signal, can be also represented as follows

![Adaptive Quantiser](./src/adaptive-quantiser.png)

![AQF and AQB](./src/aqf-aqb.png)

The advantage of __AQF__ is that variance estimation may be accomplished more accurately, as it is operates directly on the source as opposed to a quantised (noisy) version of the source.

The advantage of __AQB__ is that the variance estimates do not need to be transmitted as side information for decoding. However, practical AQF encoders transmit variance estimates only occasionally, e.g., once per block.

There are 2 types of Variance Estimation: _Block Variance Estimation_ and _Recursive Variance Estimation_.

![Block variance estimation](./src/block-variance-estimation.png)

`N` is _learning period_ and its choice may significantly impact quantiser performance: choosing N too large prevents the quantiser from adapting to the local statistics of the input, while choosing N too small results in overly noisy AQB variance estimates and excessive AQF side information.

![Recursive variance estimation](./src/recursive-variance-estimation.png)

Here `α` is forgetting factor in range `0 < α < 1` and typically near to 1.
