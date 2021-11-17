FROM ubuntu:xenial

# for easy upgrade later. ARG variables only persist during build time.
ARG VERSION="1.2"

LABEL base.image="ubuntu:xenial"
LABEL dockerfile.version="1"
LABEL software="KrakenTools"
LABEL software.version="1.2"
LABEL description="Support scripts for Kraken taxonomic sequence classifier"
LABEL website="https://github.com/jenniferlu717/KrakenTools"
LABEL license="https://github.com/jenniferlu717/KrakenTools/blob/master/LICENSE"
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

# Download KrakenTools, unpack, and install
RUN wget https://github.com/jenniferlu717/KrakenTools/archive/refs/tags/v${VERSION}.tar.gz && \
 tar -xzf v${VERSION}.tar.gz && \
 rm -rf v${VERSION}.tar.gz && \
 cd KrakenTools-${VERSION}

ENV PATH="$PATH:/KrakenTools-${VERSION}" \
    LC_ALL=C

WORKDIR /data
