### 1. Introduction to Docker

**Keywords:** Docker, Docker Image, Data Pipeline, Advantages of Docker, Reproducibility, Integration tests.

**Docker** delivers software in packages in called *containers.* These *containers* are isolated from one another. If we run a data pipeline inside a container, it is virtually isolated from the rest of the things running on the computer.

**Data pipeline:** Gets in Data → Processes Data → Generates more Data!

![what is docker](./intro_to_docker/docker_1.png)

Docker allows to run multiple databases and multiple operations in isolated environment inside the same host computer without creating conflict.

*pgAdmin allows you to communicate with the Postgres db.*

An advantage of docker is reproducibility, which allows you to create a docker image which is a snapshot (literally and in the technical sense) of your environment that contains instructions to set up an isolated docker environment.
![docker example](./intro_to_docker/docker_2.png)

We can run the container we have created through the docker image where we have specified and configured the environment beyond the host computer and essentially everywhere like - Google Cloud (Kubernetes), AWS Batch, etc.

Docker Image ensures reproducibility regardless of the machine as the images are identical. We can specify OS, programming languages, packages, database type, tools etc. This solves the problem of *"Works on my computer but NoT iN yOuRs."*

![docker_3](/Users/shikailiu/Desktop/study_notes/Intro_to_docker/docker_3.png)

### Image vs Container

#### Docker Image

A Docker image is essentially made up of multiple layers of read-only file systems, with each layer capturing the changes from the one below it. Together, these layers constitute the image which includes the code, libraries, environment variables, configuration files, and other dependencies required to run a container. The image itself is static when not running, and you can think of it as the "blueprint" for a container.

#### Docker Container

When a Docker image is run (for example, when you execute the `docker run` command), it becomes a container. A container can be understood as an instantiated object of an image; it adds a writable layer on top of the image where all changes made to the running container (such as file modifications and creation of new files) occur. The container encapsulates everything required to run the application, including the application itself and its runtime environment. It's an isolated, executable environment.

Containers can be thought of as running processes that are isolated from the host machine and from other containers. Each container has its own filesystem, networking configuration, and isolated process space.

#### Summary

So, you can envision a Docker image as a snapshot of an application with its dependencies and environment, while a container is the live, running state of that snapshot. Containers are dynamic, live, and interactive. When a container stops running, any changes made to the writable layer can be committed back into a new image layer, creating a new image—this process is foundational to how images are updated and iterated upon.

#### 1.1 Why care about Docker

1. Local Experiments: Helps to run things locally like your database also helps with testing like integration testing.
2. Integration Tests (CI/CD)
3. Reproducibility: Docker makes things run everywhere regardless of what you are using.
4. Running Pipelines on the Cloud (AWS Batch, Kubernetes Jobs)
5. Spark
6. Serverless (AWS Lambda, Google Functions)

*Integration testing is the phase in software testing in which individual software modules are combined and tested as a group.*

### Setting up Docker
For MacOS, besides the docker CLI, a docker desktop is also required to run the **docker daemon**, to use docker, the docker desktop should be started.

### Docker Run
Once you install docker, you can test if docker is installed properly you can run the following command in your terminal -

```shell
docker run hello-world
```

This will -
1. The Docker client contacted the Docker daemon.
2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (arm64v8)
3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

You can run another command, `docker run -it ubuntu bash`

`it` means interactive mode. `ubuntu` is the image you run, `bash` is the command you are running. Now essentially have a containerized linux commandline inside the commandline you have run the command line in!! To exit this container run ```exit```.

#### Entrypoint















### Reference

1. https://github.com/DataTalksClub/data-engineering-zoomcamp/tree/main/01-docker-terraform
2. https://www.youtube.com/watch?v=EYNwNlOrpr0&list=PL3MmuxUbc_hJed7dXYoJw8DoCuVHhGEQb&index=5
3. 