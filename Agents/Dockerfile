FROM maven:3.9.8-eclipse-temurin-17

USER root

ENV LANG=en_US.UTF-8 \
    LANGUAGE=en_US:en \
    LC_ALL=en_US.UTF-8

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        tzdata \
        curl \
        ca-certificates \
        fontconfig \
        locales \
        git \
        docker.io \
    && echo "en_US.UTF-8 UTF-8" > /etc/locale.gen \
    && locale-gen en_US.UTF-8 \
    && rm -rf /var/lib/apt/lists/*

# Inherit the upstream Maven image ENTRYPOINT/CMD.
# The base image already includes Maven, JDK 11, and the official Maven entrypoint.
