ARG SYSTEM=ubuntu
ARG VERSION=18.04

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
        curl \
        libstdc++6 && \
        apt-get clean --yes && rm -rf /var/lib/apt/lists/*

ARG CROSSTOOL_NG_VERSION=1.24.0
RUN git clone --branch ${CROSSTOOL_NG_VERSION} --depth 1 https://github.com/crosstool-ng/crosstool-ng.git && \
    cd crosstool-ng && \
    ./bootstrap && \
    ./configure && \
    make && \
    make install && \
    cd .. && rm -rf crosstool-ng

RUN groupadd -g 4242 awesome && useradd -r -u 4242 --create-home -g awesome awesome
RUN echo "Set disable_coredump false" >> /etc/sudo.conf

USER awesome

ENTRYPOINT ["ct-ng"]
