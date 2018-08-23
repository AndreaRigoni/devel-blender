include $(top_srcdir)/Common.mk

# Disable any target be executed inside docker image here
NODOCKERBUILD += %

DOCKERFILE = Dockerfile

IMAGE_NAME    = devel-blender
IMAGE_VERSION = 0.1
IMAGE_VENDOR  = consorziorfx

IMAGE = $(IMAGE_VENDOR)/$(IMAGE_NAME):$(IMAGE_VERSION)

#.PHONY: .dockerignore
.dockerignore:
	@ cat > $@ << EOF
	*
	!$(DOCKERFILE)
	EOF

build: ##@docker build image
build: $(DOCKERFILE)
	@ docker build -t $(IMAGE) -f $< .

push: ##@docker push image to dockerhub
push: build
	@ docker push $(IMAGE)

