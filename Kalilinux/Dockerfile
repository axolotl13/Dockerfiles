#Contenedor v.1.0
FROM kalilinux/kali-rolling:latest

ARG DEBIAN_FRONTEND=noninteractive

RUN apt update && \
  apt list --upgradable && \
  apt install -y \
  iw \
  apache2 \
  python3 \
  python3-pip \
  aircrack-ng \
  pciutils \
  kmod \
  procps \
  iproute2 \
  net-tools \
  vim 
  #set \
EXPOSE 80
CMD /usr/sbin/apache2ctl -D FOREGROUND
