FROM ubuntu:xenial

# for easy upgrade later. ARG variables only persist during build time.
ARG VERSION="2.6.2"

LABEL base.image="ubuntu:xenial"
LABEL dockerfile.version="1"
LABEL software="Bracken"
LABEL software.version="2.6.2"
LABEL description="Taxonomic sequence classifier"
LABEL website="https://github.com/jenniferlu717/Bracken"
LABEL license="https://github.com/jenniferlu717/Bracken/blob/master/LICENSE"
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

# Download Bracken, unpack, and install
RUN wget https://github.com/jenniferlu717/Bracken/archive/refs/tags/v${VERSION}.tar.gz && \
 tar -xzf v${VERSION}.tar.gz && \
 rm -rf v${VERSION}.tar.gz && \
 cd Bracken-${VERSION} && \
 bash install_bracken.sh . && \
 mkdir /data /bracken-db

ENV PATH="$PATH:/bracken-${VERSION}" \
    LC_ALL=C

WORKDIR /data
