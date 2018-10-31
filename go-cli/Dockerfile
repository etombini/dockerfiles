FROM etombini/go:0-latest

LABEL maintainer "Elvis Tombini <elvis@mapom.me>"
ENV DEBIAN_FRONTEND noninteractive

ENV HOME /home/user
RUN useradd --create-home --home-dir $HOME --shell /bin/bash user \
 && chown -R user:user $HOME 

ENV SHELL /bin/bash

USER user
WORKDIR $HOME

