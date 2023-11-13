FROM ubuntu:22.04

ENV DEBIAN_FRONTEND noninteractive

RUN apt update && apt install -y \
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
RUN apt install -y \
    tmux \
    tree \
    ruby-full \
    pkg-config \
    libssl-dev \
    liblzma-dev \
    autoconf \
    elfutils

# user setting
RUN useradd -m pwn && echo "pwn:pwn" | chpasswd && adduser pwn sudo
RUN echo '%sudo ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers
USER pwn
WORKDIR /home/pwn

# Radare2
RUN git clone --depth 1 https://github.com/radare/radare2.git ~/radare2
RUN ~/radare2/sys/install.sh

# GEF
# TODO: https://github.com/hugsy/gef/issues/195
ENV LC_CTYPE C.UTF-8
# bash -c "$(curl -fsSL https://gef.blah.cat/sh)"
RUN bash -c "$(curl -fsS https://raw.githubusercontent.com/hugsy/gef/dev/scripts/gef.sh)" _ dev

# pwntools
RUN pip install pwntools
ENV PATH /home/pwn/.local/bin:$PATH

# PyCryptodome
RUN pip install pycryptodome

# OneGadget
# (depends on ruby-full)
RUN sudo gem install one_gadget

# tmux
RUN curl https://raw.githubusercontent.com/minaminao/dotfiles/master/.tmux.conf -o .tmux.conf
RUN echo "tmux" >> .bashrc

# PatchELF
# (depends on autoconf)
RUN git clone --depth 1 https://github.com/NixOS/patchelf.git ~/patchelf
WORKDIR /home/pwn/patchelf
RUN ./bootstrap.sh 
RUN ./configure
RUN make
RUN make check
RUN sudo make install
WORKDIR /home/pwn

# # Rust (for pwninit)
# SHELL ["/bin/bash", "-c"]
# RUN curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs -o rustup.sh 
# RUN chmod +x rustup.sh
# RUN ./rustup.sh -y
# RUN source "/home/pwn/.cargo/env"

# # pwninit
# # (depends on rust, pkg-config, libssl-dev, liblzma-dev, elfutils)
# RUN cargo install pwninit
