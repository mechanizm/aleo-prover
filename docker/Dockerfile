# ========================
# BASE SETUP
# ========================
FROM --platform=linux/amd64 ubuntu:18.04 as base
ARG ARCH=linux/amd64
RUN mkdir -p /aleo_miner
WORKDIR /aleo_miner

# ========================
# LIBS
# ========================
RUN apt-get update -q
RUN DEBIAN_FRONTEND=noninteractive TZ=Etc/UTC apt-get -y install tzdata
RUN apt install -y make
RUN apt install -y clang
RUN apt install -y pkg-config
RUN apt install -y libssl-dev
RUN apt install -y build-essential
RUN apt install -y gcc
RUN apt install -y xz-utils
RUN apt install -y git
RUN apt install -y curl
RUN apt install -y wget
RUN apt install -y jq
RUN apt install -y llvm

RUN apt install -y apt-utils
RUN apt-get install -y ufw
RUN apt install -y nano
RUN apt-get install -y python3
RUN apt-get install -y iputils-ping

RUN apt-get install -y software-properties-common

RUN curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y --default-toolchain nightly

RUN echo 'source $HOME/.cargo/env' >> $HOME/.bashrc
ENV PATH="/root/.cargo/bin:${PATH}"

COPY . /aleo_miner

RUN cargo build --release

