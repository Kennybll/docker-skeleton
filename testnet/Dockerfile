FROM ubuntu:16.04

RUN apt update

RUN apt install -y sudo git clang-4.0 lldb-4.0 libclang-4.0-dev cmake make automake libbz2-dev libssl-dev \
	libgmp3-dev autotools-dev build-essential libicu-dev python2.7-dev python3-dev autoconf libtool \
	curl zlib1g-dev doxygen graphviz 


RUN mkdir -p /telos/src && \
	cd /telos/src && \
	git clone https://github.com/Telos-Foundation/telos && \
	cd telos && \
	git checkout oak-v1.6.0-rc && \
	git submodule update --init --recursive && \
	./telos_build.sh && \
	./telos_install.sh

WORKDIR /telos/data

