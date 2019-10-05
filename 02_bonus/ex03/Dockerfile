# setup environment for C program, compile it and run

FROM alpine

ARG program=main.c
ARG executable=a.out

ENV PROGRAM $program
ENV EXECUTABLE $executable

RUN apk update && apk upgrade
RUN apk add build-base 

COPY $PROGRAM main.c

RUN gcc -o $EXECUTABLE main.c

CMD ./$EXECUTABLE

# test
# docker build -t c-program --build-arg program=main.c --build-arg executable=test . 
# docker run c-program
