FROM ubuntu:vivid

ENV DEBIAN_FRONTEND noninteractive

# Usual update / upgrade
RUN apt-get update && apt-get upgrade -q -y && apt-get dist-upgrade -q -y

# Let our containers upgrade themselves
RUN apt-get install -q -y unattended-upgrades

# Install usual tools
RUN apt-get install -q -y wget vim netcat

# Install kibana
RUN cd /opt && \
    wget https://download.elastic.co/kibana/kibana/kibana-4.1.1-linux-x64.tar.gz && \
    tar -xzvf ./kibana-4.1.1-linux-x64.tar.gz && \
    mv kibana-4.1.1-linux-x64 kibana && \
    rm kibana-4.1.1-linux-x64.tar.gz

# Add configurations
ADD conf/kibana.yml /opt/kibana/config/kibana.yml
ADD entrypoint.sh /entrypoint.sh

EXPOSE 5601

ENTRYPOINT ["/entrypoint.sh"]
