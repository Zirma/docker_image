FROM ubuntu:xenial

MAINTAINER 2add2minus5 <laurent.escalier.at.scalable-design.com>

RUN apt-get update \
 && apt-get install -y software-properties-common \
     git \
     wget \
     libgl1-mesa-dri \
     menu \
     net-tools \
     openbox \
     python-pip \
     sudo \
     supervisor \
     tint2 \
     x11-xserver-utils \
     x11vnc \
     xinit \
     xserver-xorg-video-dummy \
     xserver-xorg-input-void \
     websockify \
 && rm -f /usr/share/applications/x11vnc.desktop \
 && apt-get remove -y python-pip \
 && wget https://bootstrap.pypa.io/get-pip.py \
 && python get-pip.py \
 && pip install supervisor-stdout \
 && apt-get -y clean \
 && apt-add-repository -y ppa:freecad-maintainers/freecad-daily \
 && apt-get update \
 && apt-get install -y freecad-daily \
 \
 && apt-get clean

RUN adduser --disabled-password --quiet --gecos '' freecad
RUN usermod -aG video freecad
USER freecad
CMD freecad-daily
