FROM ubuntu:20.04

RUN apt-get update && apt-get -y install sudo git iproute2

RUN useradd -s /bin/bash -d /opt/stack -m stack && \
    echo "stack ALL=(ALL) NOPASSWD: ALL" | sudo tee /etc/sudoers.d/stack

USER stack

WORKDIR /home/stack

RUN git clone https://opendev.org/openstack/devstack

COPY local.conf devstack/local.conf

WORKDIR /home/stack/devstack

RUN bash stack.sh

WORKDIR /home/stack

CMD sleep 120
