It's recommended to use the  ```chaosiq/chaostoolkit``` Docker image from Docker Hub, which is
provided by ChaosIQ. However if you want to build a customer Docker image, so you can add your own extensions
the following can be used as a starter for your own Dockerfile:

```
FROM chaostoolkit/chaostoolkit

RUN apk update && \
    apk add --virtual build-deps libffi-dev openssl-dev gcc python3-dev musl-dev && \
    pip install --no-cache-dir chaostoolkit-kubernetes && \
    pip install --no-cache-dir chaosiq-cloud && \
    apk del build-deps && \
    rm -rf /tmp/* /root/.cache

ADD . /home/svc

WORKDIR /home/svc
```

Add the above to a ```Dockerfile```, it can the be built with:

```
docker build -t my/chaostoolkit .
```

With the above Dockerfile we have added the chaostoolkit-kubernetes as an example customization, you can confirm this has been included by running:

```bash
docker run my/chaostoolkit info extensions
```
You should get an output showing you the Docker image includes the ```chaostoolkit-kubernetes``` extension.

Once you have built your local Docker image you can use your custom image in place of the ChaosIQ chaosiq/chaostoolkit image. If you are following the section
on [How to Run with ChaosIQ with Docker](/chaosiq-on-docker/chaosiq-on-docker-intro/) just replace chaosiq/chaostoolkit with your custom image name (my/chaostoolkit).
