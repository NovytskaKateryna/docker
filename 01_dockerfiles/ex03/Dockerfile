FROM ubuntu:18.04

RUN apt-get -y update && apt-get -y upgrade
RUN apt-get -y install wget ca-certificates openssh-server 

# install Postfix to send notification emails
RUN apt-get install -y postfix

# add the GitLab package repository
RUN wget https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh
RUN chmod 777 script.deb.sh && ./script.deb.sh

# install the GitLab package
RUN apt-get install -y gitlab-ce

# Missing Time Zone Data /usr/share/zoneinfo
RUN apt update && apt install -y tzdata && \
  apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

EXPOSE 443 80 22

ENTRYPOINT (/opt/gitlab/embedded/bin/runsvdir-start &) \
&& gitlab-ctl reconfigure \
&& tail -f /dev/null

# (/opt/gitlab/embedded/bin/runsvdir-start &) -> fix the gitlab-ctl reconfigure command freeze on the instruction ruby_block[supervise_redis_sleep] action run
# gitlab-ctl reconfigure -> save and reconfigure GitLab
# tail -f /dev/null -> view live log updates of GitLab logs

# build image: docker build -t ex03 .
# run container: docker run --name gitlab -it --rm -p 80:80 -p 8022:22 -p 443:443 --privileged ex03

# Tests :
# go to https://$(docker-machine ip Char) and register (it could be really slow: reload when getting 502)
# NB : the reset password page (first page) creates a user 'root' with the password you entered
