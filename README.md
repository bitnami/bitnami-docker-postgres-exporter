
# What is PostgreSQL Exporter?

PostgreSQL Exporter is a simple server that scrapes PostgreSQL metrics endpoint and exports them as Prometheus metrics.

[https://github.com/wrouesnel/postgres_exporter](https://github.com/wrouesnel/postgres_exporter)

# TL;DR;

```bash
$ docker run --name postgres-exporter bitnami/postgres-exporter:latest
```

# Why use Bitnami Images?

* Bitnami closely tracks upstream source changes and promptly publishes new versions of this image using our automated systems.
* With Bitnami images the latest bug fixes and features are available as soon as possible.
* Bitnami containers, virtual machines and cloud images use the same components and configuration approach - making it easy to switch between formats based on your project needs.
* All our images are based on [minideb](https://github.com/bitnami/minideb) a minimalist Debian based container image which gives you a small base container image and the familiarity of a leading linux distribution.
* All Bitnami images available in Docker Hub are signed with [Docker Content Trust (DTC)](https://docs.docker.com/engine/security/trust/content_trust/). You can use `DOCKER_CONTENT_TRUST=1` to verify the integrity of the images.
* Bitnami container images are released daily with the latest distribution packages available.


> This [CVE scan report](https://quay.io/repository/bitnami/postgres-exporter?tab=tags) contains a security report with all open CVEs. To get the list of actionable security issues, find the "latest" tag, click the vulnerability report link under the corresponding "Security scan" field and then select the "Only show fixable" filter on the next page.

# Why use a non-root container?

Non-root container images add an extra layer of security and are generally recommended for production environments. However, because they run as a non-root user, privileged tasks are typically off-limits. Learn more about non-root containers [in our docs](https://docs.bitnami.com/containers/how-to/work-with-non-root-containers/).

# How to deploy PostgreSQL exporter in Kubernetes?

You can find an example for testing in the file `test.yaml`. To launch this sample file run:

```bash
$ kubectl apply -f test.yaml
```

> NOTE: If you are pulling from a private containers registry, replace the image name with the full URL to the docker image. E.g.
>
> - image: 'your-registry/image-name:your-version'

# Supported tags and respective `Dockerfile` links

> NOTE: Debian 8 images have been deprecated in favor of Debian 9 images. Bitnami will not longer publish new Docker images based on Debian 8.

Learn more about the Bitnami tagging policy and the difference between rolling tags and immutable tags [in our documentation page](https://docs.bitnami.com/containers/how-to/understand-rolling-tags-containers/).


* [`0-debian-9`, `0.8.0-debian-9-r23`, `0`, `0.8.0`, `0.8.0-r23`, `latest` (0/debian-9/Dockerfile)](https://github.com/bitnami/bitnami-docker-postgres-exporter/blob/0.8.0-debian-9-r23/0/debian-9/Dockerfile)

Subscribe to project updates by watching the [bitnami/postgres-exporter GitHub repo](https://github.com/bitnami/bitnami-docker-postgres-exporter).

# Get this image

The recommended way to get the Bitnami PostgreSQL Exporter Docker Image is to pull the prebuilt image from the [Docker Hub Registry](https://hub.docker.com/r/bitnami/postgres-exporter).

```bash
$ docker pull bitnami/postgres-exporter:latest
```

To use a specific version, you can pull a versioned tag. You can view the [list of available versions](https://hub.docker.com/r/bitnami/postgres-exporter/tags/) in the Docker Hub Registry.

```bash
$ docker pull bitnami/postgres-exporter:[TAG]
```

If you wish, you can also build the image yourself.

```bash
$ docker build -t bitnami/postgres-exporter:latest 'https://github.com/bitnami/bitnami-docker-postgres-exporter.git#master:0/debian-9'
```

# Connecting to other containers

Using [Docker container networking](https://docs.docker.com/engine/userguide/networking/), a different server running inside a container can easily be accessed by your application containers and vice-versa.

Containers attached to the same network can communicate with each other using the container name as the hostname.

## Using the Command Line

### Step 1: Create a network

```bash
$ docker network create postgres-exporter-network --driver bridge
```

### Step 2: Launch the PostgreSQL Exporter container within your network

Use the `--network <NETWORK>` argument to the `docker run` command to attach the container to the `postgres-exporter-network` network.

```bash
$ docker run --name postgres-exporter-node1 --network postgres-exporter-network bitnami/postgres-exporter:latest
```

### Step 3: Run another containers

We can launch another containers using the same flag (`--network NETWORK`) in the `docker run` command. If you also set a name to your container, you will be able to use it as hostname in your network.


# Configuration

Find all the configuration flags in [the postgres_exporter official documentation](https://github.com/wrouesnel/postgres_exporter#flags).

# Logging

The Bitnami PostgreSQL Exporter Docker image sends the container logs to `stdout`. To view the logs:

```bash
$ docker logs postgres-exporter
```

You can configure the containers [logging driver](https://docs.docker.com/engine/admin/logging/overview/) using the `--log-driver` option if you wish to consume the container logs differently. In the default configuration docker uses the `json-file` driver.

# Maintenance

## Upgrade this image

Bitnami provides up-to-date versions of postgres-exporter, including security patches, soon after they are made upstream. We recommend that you follow these steps to upgrade your container.

### Step 1: Get the updated image

```bash
$ docker pull bitnami/postgres-exporter:latest
```

### Step 2: Stop the running container

Stop the currently running container using the command

```bash
$ docker stop postgres-exporter
```

### Step 3: Remove the currently running container

```bash
$ docker rm -v postgres-exporter
```

### Step 4: Run the new image

Re-create your container from the new image.

```bash
$ docker run --name postgres-exporter bitnami/postgres-exporter:latest
```

# Contributing

We'd love for you to contribute to this container. You can request new features by creating an [issue](https://github.com/bitnami/bitnami-docker-postgres-exporter/issues), or submit a [pull request](https://github.com/bitnami/bitnami-docker-postgres-exporter/pulls) with your contribution.

# Issues

If you encountered a problem running this container, you can file an [issue](https://github.com/bitnami/bitnami-docker-postgres-exporter/issues). For us to provide better support, be sure to include the following information in your issue:

- Host OS and version
- Docker version (`docker version`)
- Output of `docker info`
- Version of this container
- The command you used to run the container, and any relevant output you saw (masking any sensitive information)

# License
Copyright (c) 2019 Bitnami

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
