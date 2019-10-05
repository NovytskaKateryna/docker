FROM debian

# accept the license agreement 
ENV TS3SERVER_LICENSE=accept

# install utilities necessary for installing teamspeak
RUN apt-get update && apt-get upgrade -y
RUN apt-get install -y wget bzip2 

# download archive with Teamspeak server 
RUN wget https://files.teamspeak-services.com/releases/server/3.9.1/teamspeak3-server_linux_amd64-3.9.1.tar.bz2
# unpack archive
RUN tar xfv teamspeak3-server_linux_amd64-3.9.1.tar.bz2 

WORKDIR teamspeak3-server_linux_amd64

# at runtime container will listen on the specified network ports: 
#  9987 default voice
# 10011 server query
# 30033 file transport
EXPOSE 9987/udp 10011 30033

# startup the server
CMD ["./ts3server_minimal_runscript.sh"]

# build image: docker build -t ex01 .
# run container in background: docker run -d --name teamspeak -p 9987:9987 -p 10011:10011 -p 30033:30033 ex01
# print logs to look up for login and password: docker logs teamspeak
