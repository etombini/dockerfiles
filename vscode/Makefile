
REGISTRY = etombini
IMAGE = vscode
VERSION = 0
RELEASE = 3

BIN_PREFIX ?= ~/bin


dep:
	@docker image inspect etombini/go:latest > /dev/null || (echo "must build image etombini/go" && exit 1)

build: dep
	docker build -t $(REGISTRY)/$(IMAGE):$(VERSION)-$(RELEASE) .
	docker tag $(REGISTRY)/$(IMAGE):$(VERSION)-$(RELEASE) $(REGISTRY)/$(IMAGE):$(VERSION)-latest
	docker tag $(REGISTRY)/$(IMAGE):$(VERSION)-$(RELEASE) $(REGISTRY)/$(IMAGE):latest

push: Dockerfile
	docker push $(REGISTRY)/$(IMAGE):$(VERSION)-$(RELEASE)
	docker push $(REGISTRY)/$(IMAGE):$(VERSION)-latest
	docker push $(REGISTRY)/$(IMAGE):latest

run:
	echo ${HOME}
	docker run -d --rm \
		-v /etc/localtime:/etc/localtime:ro \
		-v /tmp/.X11-unix:/tmp/.X11-unix \
		-v ${HOME}:/home/user \
		-v /var/run/docker.sock:/var/run/docker.sock \
		-e "DISPLAY=unix${DISPLAY}" \
		--device /dev/dri \
		--name vscode \
		${REGISTRY}/${IMAGE}:${VERSION}-${RELEASE} /usr/share/code/code


install: build
	@echo "#! /bin/bash\\n\\n\
docker run -d --rm \\\\\n\
    -v /etc/localtime:/etc/localtime:ro \\\\\n\
    -v /tmp/.X11-unix:/tmp/.X11-unix \\\\\n\
    -v \$${HOME}:/home/user \\\\\n\
    -v /var/run/docker.sock:/var/run/docker.sock \\\\\n\
    -e "DISPLAY=unix\$${DISPLAY}" \\\\\n\
    -e GOPATH=/home/user/etoinc/go \\\\\n\
    --device /dev/dri \\\\\n\
    --name vscode \\\\\n\
    ${REGISTRY}/${IMAGE} /usr/share/code/code" > ${BIN_PREFIX}/vscode 
	@chmod +x ${BIN_PREFIX}/vscode
