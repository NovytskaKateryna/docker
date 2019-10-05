# Sample node js application, using yarn package manager

FROM alpine

RUN apk update && apk add nodejs yarn 

COPY app /app
WORKDIR /app

# install dependencies
RUN yarn install

# run application
EXPOSE 8181
CMD [ "node", "server.js" ]

# test
# docker build -t nodeapp .
# docker run -d -p 8181:8181 nodeapp
# browser: http://$(docker-machine ip <machine>):8181
# curl $(docker-machine ip <machine>):8181