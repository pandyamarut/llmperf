# llmperf

LLMPerf is a tool for benchmarking and validating the performance of LLMs.

Benchmarking: LLMPerf measures time to first token (TTFT),
inter-token latency (ITL) and requests that take longer than 3 seconds
to start returning data.

Validation: we send a simple query to the LLM and ensure the returned data
is valid. In particular it checks for inter-request cross-over
(request A gets the responses for request B).

Variation in input and output token lengths is a design parameter
since this is intended to be representative. This is because
there are some optimizations (e.g. continuous batching) that
we know work better with varying input and output length.

Please see `requirements.txt` for more details on dependency requirements.

## Upcoming refactor

This is prototype code. We are currently refactoring the code to be more
extensible (including a pluggable endpoints, varying traffic load etc).

TODO:

- Make running the benchmark not only possible from
  command line, but also possible to integrate easily into CI/CD or job scheduling
  systems.
- Control where the generated files and information go.
- Automate report generation.

## Usage

`python3 llmperf.py -r 20 -f runpod --max-tokens 100`
