FROM ubuntu:xenial

# for easy upgrade later. ARG variables only persist during build time.
ARG VERSION="3.0.13"

LABEL base.image="ubuntu:xenial"
LABEL dockerfile.version="1"
LABEL software="MetaPhlAn"
LABEL software.version="3.0.13"
LABEL description="Support scripts for Kraken taxonomic sequence classifier"
LABEL website="https://github.com/biobakery/MetaPhlAn/"
LABEL license="https://github.com/biobakery/MetaPhlAn/blob/master/LICENSE"
LABEL maintainer="Jeremy Le Coz"
LABEL maintainer.email="lecozjeremy.etu@gmail.com"

# Install dependencies and cleanup apt garbage
RUN apt-get update && apt-get -y --no-install-recommends install \
 wget \
 ca-certificates \
 zlib1g-dev \
 make \
 g++ \
 rsync && \
 rm -rf /var/lib/apt/lists/* && apt-get autoclean

# Download MetaPhlAn, unpack, and install
RUN wget https://github.com/biobakery/MetaPhlAn/archive/refs/tags/${VERSION}.tar.gz && \
 tar -xzf v${VERSION}.tar.gz && \
 rm -rf v${VERSION}.tar.gz && \
 cd MetaPhlAn-${VERSION}

ENV PATH="$PATH:/MetaPhlAn-${VERSION}/metaphlan/utils" \
    LC_ALL=C

WORKDIR /data
