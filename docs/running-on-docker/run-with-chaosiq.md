
## Running with ChaosIQ

To connect the image to ChaosIQ the Chaos Toolkit on hte Docker image will need
to be signed in to ChaosIQ.  The [Signing in to ChaosIQ][SignChaosIQ] page
describes the sign-in in full. The only difference here is, we will not use the default settings file by using following command for the sign-in step:

```bash
chaos --settings `pwd`/ctk_config/settings.yaml signin
```
The  `chaos signin` will prompt is similar to the following, when the  prompt for the token shows, paste in the ChaosIQ token:

```
(chaostk) $ chaos signin
  ChaosIQ Cloud url [https://console.chaosiq.io]:
  ChaosIQ Cloud token:
  Experiments and executions will be published to team 'Staging' in organization 'ChaosIQ'
  ChaosIQ Cloud details saved at /Users/grant/chaosiq-docker/settings.yaml
```
!!! Note
    The file path for the ```settings.yaml``` in the above will be your local working directory.

## Run Docker Image with your Settings File

Having created the settings file in the ```./ctk_config``` subdirectory you can now run:

```bash
docker run  -e "ENDPOINT_URL=https://httpstat.us/200?sleep=2000" \
-v `pwd`/ctk:/home/svc  -v `pwd`/ctk_config:/tmp/settings chaosiq/chaostoolkit \
 --settings /tmp/settings/settings.yaml run experiment.json
```

Here we setup a volume share with the ```./ctk_config``` subdirectory on the host and ```/tmp/settings``` on the guest with the -v option.

Then we use the ```--setttings``` option with the ```chaos run``` command to use those settings.

The result of running the command will result in the experiment being published to ChaosIQ. If you login to [ChaosIQ][] and navigate to the [Executions page][ExecutionsPage] you will see the running execution:

![Execution Running][ExecutionRunning]

If the execution has completed, you can see the completed executions by selecting the Finished tab:

![Execution Running][ExecutionComplete]

If you select the details button on the most recently finished execution, you will see the execution detail:

![Execution Detail][ExecutionDetail]

Within the execution detail page if you expand the General label you can see the details of the execution and the Experiment Steady-State Hypothesis which shows the details of the Steady-State Hypothesis.

![General and SSH view][General_SSH]

[ChaosToolkit]: https://chaostoolkit.org/
[ChaosIQCloud]: https://pypi.org/project/chaosiq-cloud/
[InstallCtk]: /gettingstarted/prerequisites
[SignChaosIQ]: /gettingstarted/signin/
[ChaosIQ]: https://console.chaosiq.io
[ChaosIQTokens]:https://console.chaosiq.io/tokens
[ExecutionsPage]: https://console.chaosiq.io/ChaosIQ/executions/finished
[ExecutionRunning]: ./images/execution-running.png
[ExecutionComplete]: ./images/executions-page.png
[ExecutionDetail]: ./images/execution-detail.png
[General_SSH]: ./images/general-ssh-view.png