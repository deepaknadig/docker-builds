FROM deepnadig/onos-ci:latest
MAINTAINER Deepak Nadig Anantha <deepnadig@gmail.com>

ENV DEBIAN_FRONTEND noninteractive

# Set the environment variables 
ENV HOME /root 
ENV JAVA_HOME /usr/lib/jvm/java-8-oracle 
ENV ONOS_ROOT /src/onos 
ENV KARAF_VERSION 3.0.5 
ENV KARAF_ROOT /root/onos/apache-karaf-3.0.5 
ENV KARAF_LOG /root/onos/apache-karaf-3.0.5/data/log/karaf.log 
ENV BUILD_NUMBER docker 
ENV PATH $PATH:$KARAF_ROOT/bin

RUN apt-get install -y net-tools
# Ports 
# 6653 - OpenFlow 
# 8181 - GUI 
# 8101 - ONOS CLI 
# 9876 - ONOS CLUSTER COMMUNICATION 

EXPOSE 6653 8181 8101 9876 

RUN cp /src/onos/tools/dev/bash_profile /root/bash_profile
WORKDIR /root
RUN cat bash_profile >> .bashrc 
RUN /bin/bash -c 'echo ONOS_IP="$(hostname --ip-address)" >> .bashrc ; echo $ONOS_IP'
RUN /bin/bash -c 'source $HOME/.bashrc ;'


#~ CMD onos $ONOS_IP
	
# Change to /root directory 
#~ WORKDIR /root 

#~ RUN git clone https://git.deepaknadig.com/deepak/OpenSec.git && \
	#~ cd OpenSec
	
#~ WORKDIR /root/OpenSec
#~ RUN mvn clean install
	 #~ && \
	#~ onos-app $ONOS_IP install! target/OpenSec-1.0-SNAPSHOT.oar

