# Dockerfile for Rust app

FROM alpine

RUN apk update && apk upgrade
RUN apk add cargo

COPY app /app
WORKDIR /app

# build Rust app
RUN cargo build 

# run program
CMD ["cargo", "run"]

# test
# docker build -t myrust .
# docker run --name rustapp myrust