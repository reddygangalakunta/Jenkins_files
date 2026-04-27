# Jenkins pipeline agent image for Maven, Docker CLI, and shell scripting
FROM maven:3.9.9-eclipse-temurin-11

USER root

RUN set -eux \
    && apt-get update \
    && apt-get install -y --no-install-recommends \
        docker.io \
        git \
        bash \
        curl \
        jq \
        ca-certificates \
    && rm -rf /var/lib/apt/lists/* \
    && groupadd -g 126 jenkins || true \
    && id -u jenkins >/dev/null 2>&1 || useradd -m -u 123 -g 126 -s /bin/bash jenkins \
    && mkdir -p /workspace /home/jenkins/.m2 \
    && chown -R jenkins:jenkins /workspace /home/jenkins/.m2

USER jenkins
ENV HOME=/home/jenkins MAVEN_CONFIG="/home/jenkins/.m2"
WORKDIR /workspace
