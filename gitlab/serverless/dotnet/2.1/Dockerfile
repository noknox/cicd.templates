FROM node:12.16.1-stretch-slim

ENV SDK_VERSION=2.1
ENV PATH="${PATH}:/root/.dotnet/tools"

RUN apt-get update && \
    apt-get install -y gpg wget

RUN wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg && \
    mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/ && \
    wget -q https://packages.microsoft.com/config/debian/9/prod.list && \
    mv prod.list /etc/apt/sources.list.d/microsoft-prod.list && \
    chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg && \
    chown root:root /etc/apt/sources.list.d/microsoft-prod.list

RUN apt-get install -y apt-transport-https ca-certificates && \
    apt-get update && \
    apt-get install -y dotnet-sdk-${SDK_VERSION} && \
    apt remove -y gpg wget && \
    rm -rf /var/lib/apt/lists/*

RUN apt-get update && \
    apt-get install -y jq wget zip && \
    wget "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -O "awscliv2.zip" && \
    unzip awscliv2.zip && \
    ./aws/install && \
    rm -rf .aws && \
    apt-get remove -y wget zip && \
    rm -rf /var/lib/apt/lists/* && \
    npm install -g serverless && \
    dotnet tool install --global Amazon.Lambda.Tools