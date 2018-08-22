include $(top_srcdir)/Common.mk

# Disable any target be executed inside docker image here
NODOCKERBUILD += %

DOCKERFILE = Dockerfile

IMAGE_NAME    = devel-blender
IMAGE_VERSION = 0.1

#.PHONY: .dockerignore
.dockerignore:
	@ cat > $@ << EOF
	*
	!$(DOCKERFILE)
	EOF

build: ##@docker build image
build: $(DOCKERFILE)
	@ docker build -t $(IMAGE_NAME):$(IMAGE_VERSION) -f $< .

push: ##@docker push image to dockerhub
push: build
	@ docker push rigoni/$(IAMGE_NAME):$(IMAGE_VERSION)
