FROM etombini/go:0-latest

LABEL maintainer "Elvis Tombini <elvis@mapom.me>"
ENV DEBIAN_FRONTEND noninteractive



# Install vscode
RUN apt-get update \
 && apt-get install -y \
    curl \
    apt-transport-https \
    apt-utils \
    gpg \
 && apt-get upgrade -yqq \
 && apt-get clean

RUN curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg \
 && mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg \
 && echo "deb [arch=amd64] https://packages.microsoft.com/repos/vscode stable main" > /etc/apt/sources.list.d/vscode.list

RUN apt-get update \
 && apt-get install -y \
    bash \
    git \
    code \
    libasound2 \
    libxtst6 \
    openssh-client \
    --no-install-recommends

RUN echo "$PATH"

ENV HOME /home/user
RUN useradd --create-home --home-dir $HOME --shell /bin/bash user \
 && chown -R user:user $HOME 

ENV SHELL /bin/bash

USER user

