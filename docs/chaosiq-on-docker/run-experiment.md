
## ChaosIQ Docker image

ChaosIQ have made the  [chaosiq/chaostoolkit](https://hub.docker.com/r/chaosiq/chaostoolkit) Docker image available on docker hub, you can download it with:

```bash
docker pull chaosiq/chaostoolkit
```

This will make the image available in your own Docker environment.


## Run an Experiment on the ChaosIQ Docker image

The ChaosIQ Docker image uses ```/home/svc``` as its working directory, we will use this to pass experiments to the docker image and to share the ```chaostoolkit.log``` and the ```journal.json``` files with the host. In your working directory create a subdirectory ```/ctk```. You will then be able to execute and experiment with the following command:

```bash
docker run  -e "ENDPOINT_URL=https://httpstat.us/200?sleep=2000" \
-v `pwd`/ctk:/home/svc chaosiq/chaostoolkit run  \
https://raw.githubusercontent.com/open-chaos/experiment-catalog/master/local/url-responds/url-responds.json
```
The experiment used is an experiment from the open source [Experiment Catalog][ExperimentCatalog], its a useful resource to get you started with your own experiments. The experiment we are using simply probes a URL and expects a 200 success response code, the full experiment can be seen in Catalog [Url Responds Experiment][UrlResponds].


The experiment depends on an environment variable ```ENDPOINT_URL```, this is setup with the ```-e``` command line argument in the ```docker run``` command.

We are also using the ```-v``` option to mount a shared volume between our local ```./ctk``` subdirectory and the ```/home/svc``` directory on the Docker guest.

We then specify the image we are going to run and provide some command line arguments, in the above case we use the command ```run``` and provide a URL to the experiment.

The output from the above command is:

```bash
[2020-03-25 09:26:14 INFO] Validating the experiment's syntax
[2020-03-25 09:26:14 INFO] Experiment looks valid
[2020-03-25 09:26:14 INFO] Running experiment: Checks the hypothesis that a URL responds with a 200 status
[2020-03-25 09:26:14 INFO] Steady state hypothesis: Application is normal
[2020-03-25 09:26:14 INFO] Probe: application-must-respond-normally
[2020-03-25 09:26:17 INFO] Steady state hypothesis is met!
[2020-03-25 09:26:17 INFO] Action: dummy step
[2020-03-25 09:26:17 INFO] Steady state hypothesis: Application is normal
[2020-03-25 09:26:17 INFO] Probe: application-must-respond-normally
[2020-03-25 09:26:20 INFO] Steady state hypothesis is met!
[2020-03-25 09:26:20 INFO] Let's rollback...
[2020-03-25 09:26:20 INFO] No declared rollbacks, let's move on.
[2020-03-25 09:26:20 INFO] Experiment ended with status: completed
```

After running ```docker run``` command we can check the ```./ctk``` subdirectory and we will find the ```chaostoolkit.log``` and the ```journal.json``` file.

## Using a local Experiment file

We can also use a local experiment file with this approach. In the ```./ctk``` subdirectory create an ```experiment.json``` and paste in a copy of the [Url Responds Experiment][UrlRespondsRaw] and save the file. Then run:

```bash
docker run  -e "ENDPOINT_URL=https://httpstat.us/200?sleep=2000" \
  -v `pwd`/ctk:/home/svc chaosiq/chaostoolkit  run experiment.json
```

You will get the same output show above and an updated ```chaostoolkit.log``` and a new ```journal.json``` in the ```./ctk``` folder.


[UrlResponds]: https://github.com/open-chaos/experiment-catalog/tree/master/local/url-responds
[UrlRespondsRaw]: https://raw.githubusercontent.com/open-chaos/experiment-catalog/master/local/url-responds/url-responds.json
[ExperimentCatalog]: https://github.com/open-chaos/experiment-catalog