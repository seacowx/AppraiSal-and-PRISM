# PRISM

The code for **PRISM** (**PR**obabilistic **I**nference of **S**alient **M**ental States) will be released here soon.

See the [main README](../README.md#the-prism-framework) for an overview of the framework and the [paper](https://arxiv.org/abs/2607.28648) for full details.

PRISM scores hypotheses with token log-probabilities of a given target, so it needs an inference backend that exposes **prompt (echo) logprobs**, which most open-weight model servers support.
