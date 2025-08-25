# Automated Test Generation Tool

## Deliverables

An automated test generator that turns code (and/or user stories) into executable unit tests with assertions, wired into CI/CD.

## Predicted Issues & Questions

- test assistant (code coverage)
- unit tests vs integration tests
- based on user stories or the code it self
- use of AI/machinelearning?
- tests in scalar/f# maybe?
- granularity

## Draft research questions (RQs)

RQ1. Can we statically analyse code/us and automatically produce mutually exclusisive and comprhensively exhaustive tests for a functionality?

RQ2. Can we produce tests that acts in a predictable integrationally maner?

RQ3. For developers, which integration surface (PR bot, IDE plugin, CI job) yields most adoption?

RQ4. How would it compare to other automated tools and/or manual testing?

## Prior work & gaps

Strong, mature baselines exist: EvoSuite (whole test-suite generation), KLEE (symbolic execution), and Randoop (feedback-directed random testing).

Many are highly cited and open—great for head-to-head comparisons.

The opening: combining these ideas with modern CI ergonomics and better oracle inference (??), plus measuring developer acceptance in real workflows.
