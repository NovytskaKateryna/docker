# Recreate a full MEAN Stack and serve sample app

FROM ubuntu

RUN apt-get update -y && apt-get upgrade -y
RUN apt-get install -y gnupg curl npm mongodb

# install Node.js
# the following command will automatically read this script from a remote location and execute it
RUN curl -sL https://deb.nodesource.com/setup_12.x | bash -
RUN apt-get install -y nodejs

# Node.js has no dependencies, but some npm packages will probably throw errors when compiling. 
# To fix this, we need to install the build-essentials package as well
RUN apt-get install build-essential
# install Angular cli tool
RUN npm install -g @angular/cli

# test
# docker build -t mean .
# docker run --name mean-env -it --rm mean
# check environment: 
# node -v
# npm -v
# ng --version
# mkdir -p /data/db && mongod