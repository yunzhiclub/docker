FROM java:8-jdk
WORKDIR /usr/src/myapp
RUN apt-get update && apt install software-properties-common -y \
	&& add-apt-repository "deb http://ppa.launchpad.net/natecarlson/maven3/ubuntu precise main" \
	&& apt-get update && apt-get install maven3 && echo 'export M2_HOME=/usr/share/maven3' >> /etc/profile \
	 && echo 'export M2=$M2_HOME/bin' >> /etc/profile \
	 && echo 'export PATH=$M2:$PATH' >> /etc/profile && source /etc/profile