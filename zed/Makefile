
REGISTRY = etombini
IMAGE = zed
VERSION = 0
RELEASE = 1 


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
		--name zed \
		${REGISTRY}/${IMAGE}:${VERSION}-${RELEASE}	zed_free 
