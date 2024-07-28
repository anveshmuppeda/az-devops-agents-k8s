#
# Ubuntu Bionic + Docker
#
# Instructions for docker installation taken from:
# https://docs.docker.com/install/linux/docker-ce/ubuntu/
#

FROM ubuntu:bionic

# Docker install
RUN apt-get update && apt-get install --no-install-recommends -y \
       apt-transport-https \
       ca-certificates \
       curl \
       gnupg-agent \
       software-properties-common

RUN curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add -
RUN apt-key fingerprint 0EBFCD88

RUN add-apt-repository \
       "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
       $(lsb_release -cs) \
       stable"

RUN apt-get update && apt-get install --no-install-recommends -y docker-ce docker-ce-cli containerd.io

RUN apt update -y && apt upgrade -y && apt install curl git jq libicu60 -y

# Adding new user to run the build execution 
RUN adduser -D agent \
       chown agent ./ \
       # Add user "agent" to the Docker group
       && usermod -a -G docker agent

# Also can be "linux-arm", "linux-arm64".
ENV TARGETARCH="linux-x64"

WORKDIR /azp/

COPY ./start.sh ./
RUN chmod +x ./start.sh

# ENV AGENT_ALLOW_RUNASROOT="true"
USER agent

# # Set start.sh script as ENTRYPOINT.
ENTRYPOINT ["/azp/start.sh"]