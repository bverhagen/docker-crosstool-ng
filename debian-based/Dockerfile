ARG SYSTEM
ARG VERSION

FROM ${SYSTEM}:${VERSION}
MAINTAINER Bart Verhagen <barrie.verhagen@gmail.com>

RUN apt-get update && \
    apt-get install --yes \
        git \
        gcc \
        g++ \
        gperf \
        bison \
        flex \
        texinfo \
        help2man \
        make \
        libncurses5-dev \
        autoconf \
        automake \
        libtool \
        libtool-bin \
        gawk \
        wget \
        bzip2 \
        xz-utils \
        unzip \
        patch \
        libstdc++6 && \
        apt-get clean --yes && rm -rf /var/lib/apt/lists/*

ARG CROSSTOOL_NG_VERSION
RUN git clone --branch ${CROSSTOOL_NG_VERSION} --depth 1 https://github.com/crosstool-ng/crosstool-ng.git && \
    cd crosstool-ng && \
    ./bootstrap && \
    ./configure && \
    make && \
    make install && \
    cd .. && rm -rf crosstool-ng

ENTRYPOINT ["ct-ng"]
