FROM java:8-jdk
WORKDIR /usr/src/myapp
RUN apt-get update && apt install software-properties-common -y \
	&& add-apt-repository "deb http://ppa.launchpad.net/natecarlson/maven3/ubuntu precise main" \
	&& apt-get update && apt-get install maven3