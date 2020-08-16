FROM ubuntu:18.04

LABEL maintainer "Elvis Tombini <elvis@mapom.me>"
ENV DEBIAN_FRONTEND noninteractive

# Install go (the easy way)
# gcc for cgo
RUN apt-get update && apt-get install -y --no-install-recommends \
		ca-certificates \
		g++ \
		gcc \
		libc6-dev \
		make \
		pkg-config \
 && rm -rf /var/lib/apt/lists/*

#Needed for "go get" and pprof
RUN apt-get update && apt-get install -y --no-install-recommends \
		curl \
		git \
        mercurial \
        subversion \
        graphviz

RUN curl https://dl.google.com/go/go1.15.linux-amd64.tar.gz --output go.tgz; \
	tar -C /usr/local -xzf go.tgz; \
	rm go.tgz; \
	export PATH="/usr/local/go/bin:$PATH"; \
	go version

ENV GOPATH /go
ENV GO111MODULE on
ENV PATH $GOPATH/bin:/usr/local/go/bin:$PATH

