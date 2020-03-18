The Verification format is an experiment format that has the addition of an [Extension](https://docs.chaostoolkit.org/reference/api/experiment/#extensions). An example Verification extension is:

```json
"extensions": [
    {
        "name": "chaosiq",
        "objective_id": "48637aae-11a0-4f16-816f-55faef12d5d0",
        "verification": {
            "id": "2adfd65c-ba38-4482-a73e-eb26252e4ebc",
            "duration-of-conditions": 180,
            "frequency-of-measurement": 2
        },
        "experiment_id": "338e26f6-6ff6-42f8-a181-e7df9cbf385e"
    }
    ]
```

The extension identifies chaosiq as the vendor and then provides a number of custom properties:

*  objective_id: this provides a mapping from the Verification to an Objective.
*  verification: the Verification includes a number of further properties:
    * id: a unique identifier for the Verification.
    * duration-of-condition: this is the deration for the Verification in seconds, this is how long the Verification will run for
    * frequency-of-measurement: this is the frequency that the measurement will be taken at, in this case the measure will be taken at every 2 seconds. The steady state hypothesis in the experiment is used as the measurement.

## Example Verification


```json
{
    "title": "Staging console can survive real pod death",
    "description": "N/A",
    "configuration": {},
    "secrets": {},
    "extensions": [
        {
            "name": "chaosiq",
            "objective_id": "48637aae-11a0-4f16-816f-55faef12d5d0",
            "verification": {
                "id": "2adfd65c-ba38-4482-a73e-eb26252e4ebc",
                "duration-of-conditions": 180,
                "frequency-of-measurement": 2
            },
            "experiment_id": "338e26f6-6ff6-42f8-a181-e7df9cbf385e"
        }
    ],
    "tags": [],
    "steady-state-hypothesis": {
        "title": "Staging Console is Available",
        "probes": [
            {
                "name": "http-response-time",
                "type": "probe",
                "provider": {
                    "type": "python",
                    "module": "chaoscloud.probes.http",
                    "func": "time_http_call",
                    "arguments": {
                        "url": "https://console.chaosiq.dev"
                    }
                },
                "tolerance": {
                    "name": "http-response-time-under",
                    "type": "probe",
                    "provider": {
                        "type": "python",
                        "module": "chaoscloud.tolerances.http",
                        "func": "response_time_under",
                        "arguments": {
                            "duration": 500
                        }
                    }
                }
            }
        ]
    },
    "method": [
        {
            "name": "terminate-pods",
            "type": "action",
            "provider": {
                "type": "python",
                "module": "chaosk8s.pod.actions",
                "func": "terminate_pods",
                "arguments": {
                    "ns": "chaosiq-console",
                    "label_selector": "chaosiq-saas-backend-6755597d54-8npfz",
                    "all": false,
                    "qty": 1,
                    "rand": false
                }
            }
        }
    ]
}
```

In the full verification above:

* The verifications title and description are meant for humans and therefore should be as descriptive as possible to clarify the verifications rationale.
* Configuration and Secrets  are optional and is same as for for an [Experiment Configuration](https://docs.chaostoolkit.org/reference/api/experiment/#configuration) and [Experiment Secrets](https://docs.chaostoolkit.org/reference/api/experiment/#secrets).
* Steady State Hypothesis - this is used in this case as a measure of your system.
* Method - this is used to apply some condition to your system, in this case this is to kill a kubernetes pod.
