FROM ubuntu:bionic

LABEL maintainer "Elvis Tombini <elvis@mapom.me>"
ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && apt-get -u upgrade -y && apt-get install -y --no-install-recommends \
		ca-certificates \
        apt-utils \
		curl \
        libqtgui4 \
        libxml2 \
        shared-mime-info \
        desktop-file-utils

RUN curl https://www.zedencrypt.com/file/get/-/item_key/13802-22-7036b18e  --output zed.deb; \
    dpkg -i zed.deb

ENV HOME /home/user                                                                                           
RUN useradd --create-home --home-dir $HOME --shell /bin/bash user \                                           
 && chown -R user:user $HOME                                                                                  
                                                                                                              
ENV SHELL /bin/bash                                                                                           
                                                                                                              
USER user
