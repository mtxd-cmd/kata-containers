# Copyright (c) 2022 IBM
#
# SPDX-License-Identifier: Apache-2.0

FROM ubuntu:20.04
ENV DEBIAN_FRONTEND=noninteractive
RUN sed -i s@/archive.ubuntu.com/@/mirrors.aliyun.com/@g /etc/apt/sources.list
RUN sed -i s@/security.ubuntu.com/@/mirrors.aliyun.com/@g /etc/apt/sources.list
RUN apt-get clean
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        ca-certificates \
        curl \
        g++ \
        gcc \
        git \
        iasl  \
        make \
        python \
        python3 \
        python3-distutils \
        uuid-dev && \
    apt-get clean && rm -rf /var/lib/lists/ && \
    cd /tmp && curl -fsLO https://www.nasm.us/pub/nasm/releasebuilds/2.15.05/nasm-2.15.05.tar.gz && \
    tar xf nasm-2.15.05.tar.gz && \
    cd nasm-2.15.05 && \
    ./configure && \
    make -j"$(nproc)" && \
    make install && \
    cd /tmp && rm -r nasm-2.15.05*
