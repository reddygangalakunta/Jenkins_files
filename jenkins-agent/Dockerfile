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
    && rm -rf /var/lib/apt/lists/*

ENV MAVEN_CONFIG="/root/.m2"
WORKDIR /workspace

ENTRYPOINT ["bash"]
