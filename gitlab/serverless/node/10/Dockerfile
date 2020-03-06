FROM node:10.19.0-stretch-slim

RUN apt-get update && \
    apt-get install -y jq wget zip && \
    wget "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -O "awscliv2.zip" && \
    unzip awscliv2.zip && \
    ./aws/install && \
    rm -rf .aws && \
    apt-get remove -y wget zip && \
    rm -rf /var/lib/apt/lists/* && \
    npm install -g serverless