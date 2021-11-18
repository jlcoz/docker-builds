FROM ubuntu:xenial

# for easy upgrade later. ARG variables only persist during build time.
ARG VERSION="2.1.2"

LABEL base.image="ubuntu:xenial"
LABEL dockerfile.version="1"
LABEL software="Kraken2"
LABEL software.version="2.1.2"
LABEL description="Taxonomic sequence classifier"
LABEL website="https://github.com/DerrickWood/kraken2"
LABEL license=https://github.com/DerrickWood/kraken2blob/master/LICENSE"
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

# Download Kraken, unpack, and install
RUN wget https://github.com/DerrickWood/kraken2/archive/refs/tags/v${VERSION}.tar.gz && \
 tar -xzf v${VERSION}.tar.gz && \
 rm -rf v${VERSION}.tar.gz && \
 cd kraken2-${VERSION} && \
 bash install_kraken2.sh . && \
 mkdir /data /kraken-db

ENV PATH="$PATH:/kraken2-${VERSION}" \
    LC_ALL=C

WORKDIR /data
