FROM ghcr.io/taffish-org/debian:12

LABEL maintainer="taffish@163.com"

WORKDIR /root

ENV USER=root

RUN apt-get update && \
    apt-get install -y curl git gcc g++ make cmake build-essential catch2 \
                       python3-dev python3-pip python3-pmw python3-pyqt5.qtopengl python3-mmtf python3-websockify \
                       libglew-dev libpng-dev libfreetype6-dev libxml2-dev libmsgpack-dev libglm-dev libnetcdf-dev libopengl-dev libglut-dev libgxr-dev && \
    cd / && \
    git clone https://github.com/rcsb/mmtf-cpp.git && \
    curl -LO https://github.com/schrodinger/pymol-open-source/archive/refs/tags/v3.1.0.tar.gz && \
    tar -zxvf /v3.1.0.tar.gz && \
    mv /pymol-open-source-3.1.0 /pymol-open-source && \
    mv /mmtf-cpp/include/mmtf* /pymol-open-source/include/ && \
    cd /pymol-open-source/ && \
    python3 setup.py build install --home=/pymol-open-source-build && \
    cp -r /pymol-open-source-build/lib/python/* /usr/local/lib/python3.11/dist-packages/ && \
    cp /pymol-open-source-build/bin/pymol /usr/local/bin/ && \
    cd / && rm -r mmtf-cpp pymol-open-source pymol-open-source-build v3.1.0.tar.gz

# add gui by vnc & http by noVNC
RUN apt-get update && apt-get install -y xfce4 tightvncserver xfce4-terminal xvfb x11vnc dbus-x11 && \
    cd / && git clone https://github.com/novnc/noVNC.git
#    mkdir -p /root/.vnc && \
#    echo 'taffish2025' | vncpasswd -f > /root/.vnc/passwd && \
#    echo '#!/bin/sh'                                    >  /root/.vnc/xstartup && \
#    echo 'export DISPLAY=":1"'                          >> /root/.vnc/xstartup && \
#    echo 'xrdb /root/.Xresources'                       >> /root/.vnc/xstartup && \
#    echo 'dbus-launch --exit-with-session startxfce4 &' >> /root/.vnc/xstartup && \
#    chmod +x /root/.vnc/xstartup && \
#    echo '#!/bin/sh'                                                     >  /usr/local/bin/start-gui.sh && \
#    echo 'tightvncserver :1 -geometry 1280x720 -depth 24'                >> /usr/local/bin/start-gui.sh && \
#    echo '/noVNC/utils/novnc_proxy --vnc localhost:5901 --listen 5801 &' >> /usr/local/bin/start-gui.sh && \
#    chmod +x /usr/local/bin/start-gui.sh

ENV TAFFISH_ENV=TAFFISH
ENV TAFFISH_NAME=pymol
