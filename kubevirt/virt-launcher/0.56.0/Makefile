# This file is generated by the template.

REGISTRY?=cr.loongnix.cn
ORGANIZATION?=kubevirt
REPOSITORY?=virt-launcher
TAG?=0.56.0
LATEST?=true

IMAGE=$(REGISTRY)/$(ORGANIZATION)/$(REPOSITORY):$(TAG)
LATEST_IMAGE=$(REGISTRY)/$(ORGANIZATION)/$(REPOSITORY):latest

default: image

download:
	wget -O container-disk https://github.com/Loongson-Cloud-Community/kubevirt/releases/download/v0.56.0/container-disk
	wget -O virt-launcher https://github.com/Loongson-Cloud-Community/kubevirt/releases/download/v0.56.0/virt-launcher-v0.56.0-linux-loong64
	wget -O virt-launcher-monitor https://github.com/Loongson-Cloud-Community/kubevirt/releases/download/v0.56.0/virt-launcher-monitor-v0.56.0-linux-loong64
	wget -O virt-freezer https://github.com/Loongson-Cloud-Community/kubevirt/releases/download/v0.56.0/virt-freezer-v0.56.0-linux-loong64
	wget -O virt-probe https://github.com/Loongson-Cloud-Community/kubevirt/releases/download/v0.56.0/virt-probe-v0.56.0-linux-loong64
	wget https://github.com/Loongson-Cloud-Community/kubevirt/releases/download/v0.56.0/libvirt-8.0-rpm.tar.gz
	chmod +x container-disk virt-launcher virt-launcher-monitor virt-freezer virt-probe
	tar -zxf libvirt-8.0-rpm.tar.gz

image: download
	docker build \
		-t $(IMAGE) \
		.

clean:
	rm -rf container-disk \
		virt-launcher \
		virt-launcher-monitor \
		virt-freezer \
		virt-probe \
		libvirt-8.0-rpm.tar.gz \
		libvirt-8.0-rpm

push:
	docker push $(IMAGE)
	#latest image
	@if [ $(LATEST) = "true" ]; \
		then \
		docker tag $(IMAGE) $(LATEST_IMAGE); \
		docker push $(LATEST_IMAGE); \
	fi
