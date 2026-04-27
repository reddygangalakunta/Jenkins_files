# Jenkins Agent Image

This directory contains a Dockerfile for a Jenkins pipeline agent that includes:

- Maven 3.9.9 with Eclipse Temurin JDK 11
- Docker CLI (`docker.io`)
- Git
- Bash shell
- Curl and jq for scripts and API calls
- non-root Jenkins-compatible user support

## Build the agent image

```bash
cd /home/yashwanth-reddy/Documents/DevOps/CI_CD/jenkins-agent
docker build -t yashwanth1232/jenkins-maven-docker-agent:v1 .
```

## Push to Docker Hub

```bash
docker push yashwanth1232/jenkins-maven-docker-agent:v1
```

## Use in Jenkins pipeline

In your `JenkinsFile`, set the agent image to this Docker image and mount the Docker socket:

```groovy
pipeline {
  agent {
    docker {
      image 'yashwanth1232/jenkins-maven-docker-agent:v1'
      args '-v /var/run/docker.sock:/var/run/docker.sock'
    }
  }
  stages {
    // pipeline stages here
  }
}
```

## Notes

- The image is designed to run Maven builds and Docker commands inside the Jenkins container.
- Mounting `/var/run/docker.sock` allows the container to use the host Docker daemon.
- If you need additional tools, add them to the Dockerfile and rebuild the image.
