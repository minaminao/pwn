FROM ubuntu:22.04

ENV DEBIAN_FRONTEND noninteractive

RUN apt update -y
RUN apt install -y \
    curl \
    git \
    ltrace \
    strace \
    make \
    build-essential \ 
    python3 \
    python-is-python3 \
    python3-pip \
    vim \
    gdb \
    file \
    netcat \
    sudo \
    wget

RUN useradd -m pwn && echo "pwn:pwn" | chpasswd && adduser pwn sudo
RUN echo '%sudo ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers
USER pwn
WORKDIR /home/pwn

# https://github.com/hugsy/gef/issues/195 TODO
ENV LC_CTYPE C.UTF-8
RUN bash -c "$(curl -fsSL https://gef.blah.cat/sh)"

RUN git clone --depth 1 https://github.com/radare/radare2.git ~/radare2
RUN ~/radare2/sys/install.sh

RUN pip install pwntools
ENV PATH /home/pwn/.local/bin:$PATH

RUN pip install pycryptodome
