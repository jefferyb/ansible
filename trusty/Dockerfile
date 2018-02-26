# To build:
#   $ docker build -t jefferyb/ansible:trusty .
#
FROM ubuntu:14.04
MAINTAINER Jeffery Bagirimvano

RUN \
  echo "deb http://ppa.launchpad.net/ansible/ansible/ubuntu trusty main" | tee /etc/apt/sources.list.d/ansible.list && \
  apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 93C4A3FD7BB9C367 && \
  apt-get update && \
  apt-get install -y git ansible && \
  echo 'localhost     ansible_connection=local' > /etc/ansible/hosts && \
  echo '[local]\nlocalhost\n' >> /etc/ansible/hosts

RUN \
  mkdir /root/.ssh && \
  echo "Host *\nStrictHostKeyChecking no" > /root/.ssh/config

VOLUME /playbooks
VOLUME /root/.ssh
VOLUME /etc/ansible

WORKDIR /playbooks

CMD ansible
