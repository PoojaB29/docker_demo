# Base image for Cursor cloud/background agents.
# Do NOT copy project code here — the agent clones the repo at runtime.
FROM ubuntu:24.04

ARG DEBIAN_FRONTEND=noninteractive

# Core dev tools for building, testing, and running commands
RUN apt-get update && apt-get install -y \
    git \
    curl \
    wget \
    ca-certificates \
    gnupg \
    build-essential \
    python3 \
    python3-pip \
    python3-venv \
    nodejs \
    npm \
    vim \
    && rm -rf /var/lib/apt/lists/*

# Docker CLI (useful for a Docker learning project)
RUN install -m 0755 -d /etc/apt/keyrings \
    && curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc \
    && chmod a+r /etc/apt/keyrings/docker.asc \
    && echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu noble stable" \
       > /etc/apt/sources.list.d/docker.list \
    && apt-get update \
    && apt-get install -y docker-ce-cli docker-compose-plugin \
    && rm -rf /var/lib/apt/lists/*

# Non-root user (recommended by Cursor)
RUN useradd -m -s /bin/bash ubuntu

USER ubuntu
WORKDIR /home/ubuntu
