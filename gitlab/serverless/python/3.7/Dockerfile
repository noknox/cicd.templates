FROM node:12.16.1-stretch-slim

ENV PYTHON_VERSION=3.7.3

RUN apt update && \
    apt install -y build-essential zlib1g-dev libncurses5-dev libgdbm-dev libnss3-dev libssl-dev libreadline-dev libffi-dev wget

RUN wget https://www.python.org/ftp/python/${PYTHON_VERSION}/Python-${PYTHON_VERSION}.tar.xz -O Python-${PYTHON_VERSION}.tar.xz && \
    tar -xf Python-${PYTHON_VERSION}.tar.xz && \
    cd Python-${PYTHON_VERSION} && \
    ./configure --enable-optimizations && \
    make && \
    make install && \
    apt remove -y build-essential zlib1g-dev libncurses5-dev libgdbm-dev libnss3-dev libssl-dev libreadline-dev libffi-dev wget && \
    rm -rf /var/lib/apt/lists/*

RUN apt-get update && \
    apt-get install -y jq wget zip && \
    wget "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -O "awscliv2.zip" && \
    unzip awscliv2.zip && \
    ./aws/install && \
    rm -rf .aws && \
    apt-get remove -y wget zip && \
    rm -rf /var/lib/apt/lists/* && \
    npm install -g serverless