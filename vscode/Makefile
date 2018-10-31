
REGISTRY = etombini
IMAGE = vscode
VERSION = 0
RELEASE = 3


build: Dockerfile
	docker build -t $(REGISTRY)/$(IMAGE):$(VERSION)-$(RELEASE) .
	docker tag $(REGISTRY)/$(IMAGE):$(VERSION)-$(RELEASE) $(REGISTRY)/$(IMAGE):$(VERSION)-latest

push: Dockerfile
	docker push $(REGISTRY)/$(IMAGE):$(VERSION)-$(RELEASE)
	docker push $(REGISTRY)/$(IMAGE):$(VERSION)-latest

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
