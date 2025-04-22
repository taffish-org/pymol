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
    cd / && git clone https://github.com/novnc/noVNC.git && \
    echo 'cd /' >> /root/.bashrc && \
    echo 'echo ""' >> /root/.bashrc && \
    echo 'echo "Welcome to taffish-pymol-GUI!"' >> /root/.bashrc && \
    echo 'echo ""' >> /root/.bashrc && \
    echo 'echo "If you want to use pymol, you can run the cmd:"' >> /root/.bashrc && \
    echo 'echo "  % pymol"' >> /root/.bashrc && \
    echo 'echo ""' >> /root/.bashrc

ENV TAFFISH_ENV=TAFFISH
ENV TAFFISH_NAME=pymol
