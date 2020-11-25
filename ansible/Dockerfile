FROM ubuntu:20.04
LABEL maintainer=chanfr

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get upgrade -y

RUN apt-get install -y  apt-utils \
       locales \
       libyaml-dev \
       python3-setuptools \
       python3-pip \
       python3-yaml \
       software-properties-common \
       rsyslog systemd systemd-cron sudo iproute2 ansible

RUN apt-get install -y openssh-server sudo nano iputils-ping



RUN useradd -ms /bin/bash ansible && echo ansible:ansible | chpasswd && echo "ansible ALL=(ALL) ALL" >> /etc/sudoers

USER ansible
WORKDIR /home/ansible/
RUN ssh-keygen -f $HOME/.ssh/id_rsa -t rsa -N '' 
