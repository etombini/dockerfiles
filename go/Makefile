
REGISTRY = etombini
IMAGE = go
VERSION = 0
RELEASE = 20200815


build: Dockerfile
	docker build -t $(REGISTRY)/$(IMAGE):$(VERSION)-$(RELEASE) .
	docker tag $(REGISTRY)/$(IMAGE):$(VERSION)-$(RELEASE) $(REGISTRY)/$(IMAGE):$(VERSION)-latest 
	docker tag $(REGISTRY)/$(IMAGE):$(VERSION)-$(RELEASE) $(REGISTRY)/$(IMAGE):latest

push: Dockerfile
	docker push $(REGISTRY)/$(IMAGE):$(VERSION)-$(RELEASE)
	docker push $(REGISTRY)/$(IMAGE):$(VERSION)-latest
	docker push $(REGISTRY)/$(IMAGE):latest

run:
	docker run -i --rm \
		-v /etc/localtime:/etc/localtime:ro \
		-v /tmp/.X11-unix:/tmp/.X11-unix \
		-v ${HOME}:/home/user \
		-v /var/run/docker.sock:/var/run/docker.sock \
		-e "DISPLAY=unix${DISPLAY}" \
		--device /dev/dri \
		--name go \
		${REGISTRY}/${IMAGE}:${VERSION}-${RELEASE} go version
