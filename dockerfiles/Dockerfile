FROM ghcr.io/taffish-org/debian:12

LABEL maintainer="taffish@163.com"

WORKDIR /root

RUN apt-get update && apt-get install -y curl git gcc g++ make

RUN apt-get update && apt-get install -y cmake build-essential python3-dev python3-pip python3-pmw libglew-dev libpng-dev libfreetype6-dev libxml2-dev libmsgpack-dev python3-pyqt5.qtopengl libglm-dev libnetcdf-dev libopengl-dev libglut-dev python3-mmtf catch2 libgxr-dev

RUN git clone https://github.com/rcsb/mmtf-cpp.git && \
    curl -LO https://github.com/schrodinger/pymol-open-source/archive/refs/tags/v3.1.0.tar.gz && tar -zxvf /root/v3.1.0.tar.gz && \
    mv /root/pymol-open-source-3.1.0 /root/pymol-open-source && \
    mv /root/mmtf-cpp/include/mmtf* /root/pymol-open-source/include/ && \
    cd /root/pymol-open-source/ && python3 setup.py build install --home=/root/pymol-open-source-build && \
    cp -r /root/pymol-open-source-build/lib/python/* /usr/local/lib/python3.11/dist-packages/ && \
    cp /root/pymol-open-source-build/bin/pymol /usr/local/bin/ && \
    cd /root/ && rm -r mmtf-cpp pymol-open-source pymol-open-source-build v3.1.0.tar.gz

ENV TAFFISH_ENV=TAFFISH
ENV TAFFISH_NAME=pymol
