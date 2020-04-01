A reliability objective is something in your System that you or your customers care about and which shows that your system or part of your system is available. In Site Reliability Engineering (SRE) terms this is a Service Level Objective (SLO).
You might care that your homepage is available 99.9% of the time. You might care that your database is able to respond to a particular query under an amount of time. Or you might care that your users can interact with your system, perform some system function, 99.999% of the time as it’s super-critical! These are all Objectives, and they frame what’s important to you about your system. A good set of Objectives represents a great high-level description of how your system aims to behave, from your perspective, in order to make your users happy.

You create an Objective  from the [Objectives page](https://console.chaosiq.io/ChaosIQ/Staging/objectives) and click the `Create a New Objective` button.

If you don't currently have a team selected you will have to select a team to associate this objective with.

On the Objective form specify an Objective you care about for your system. First, you need to add a meaningful name for your Objective. An objective's name should mean something of value to the business or your customers. You can also add an optional description to elaborate on your Objective.

You can optionally add a tag to your Objective. Tags are used to filter for your objective when you are managing many Objectives.

You now specify the most important part of your objective which is a target percentage availability over a specified period, an example could be 99.5% available, over a period of 7 days. The target availability is less than 100% so this leaves a margin for error, this can be considered the Error Budget.


![Create Objective][createObjective]

[createObjective]: /gettingstarted/images/create-objective.png

The next step is to identify how you would measure your Objective. This is something in your that you can measure that is an indicator that the system is meeting its objectives.