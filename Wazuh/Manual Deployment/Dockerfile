FROM ubuntu:jammy

ENV DEBIAN_FRONTEND=noninteractive

RUN apt update
RUN apt-get install build-essential -y
RUN apt install cmake -y
RUN apt install curl -y

RUN mkdir wazuh
COPY . /wazuh

WORKDIR /wazuh/src
RUN make deps
RUN make TARGET=server

RUN chmod +x /wazuh/install.sh

WORKDIR /wazuh
COPY entrypoint.sh /usr/local/bin/
RUN chmod +x /usr/local/bin/entrypoint.sh

ENTRYPOINT ["/usr/local/bin/entrypoint.sh"]

EXPOSE 55000 1515 1514