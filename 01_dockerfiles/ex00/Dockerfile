FROM alpine

# update the index of available packages && install vim
RUN apk update && apk add vim

# open vim editor
CMD ["vim", "file"]

# to build the image: docker build --tag ex00 .
# to run the container: docker run --rm -it ex00
# check the new image: docker images
