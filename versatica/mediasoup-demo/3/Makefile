# This file is generated by the template.

REGISTRY?=cr.loongnix.cn
ORGANIZATION?=versatica
REPOSITORY?=mediasoup-demo
TAG?=3

IMAGE=$(REGISTRY)/$(ORGANIZATION)/$(REPOSITORY):$(TAG)


default: image

image:
	docker build --no-cache \
		-t $(IMAGE) \
		.

push:
	docker push $(IMAGE)
