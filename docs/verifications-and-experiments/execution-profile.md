An Experiment has a different execution profile from a Verification. When an Experiment runs it will run the [Steady State Hypothesis][SteadyStateHypothesis] at the beginning of the Experiment. It will then execute the method block in the experiment, followed by running the Steady State Hypothesis again.

A Verification on the other hand will execute in exactly the same way as the Experiment, except during the execution of the method block it will continue to run the Steady State Hypothesis at the specified frequency and for the specified duration given in the Verification extension block.

In both cases if there are any rollbacks defined these will be executed after the last Steady State Hypothesis is run.

[SteadyStateHypothesis]: https://docs.chaostoolkit.org/reference/concepts/#steady-state-hypothesis