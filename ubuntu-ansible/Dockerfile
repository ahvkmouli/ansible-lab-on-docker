FROM ubuntu:latest
LABEL maintainer "Adiraju Havish Venkata Krishna Mouli havish.moulih@gmail.com"

RUN useradd -rm -d /home/sysops -s /bin/bash -g root -G sudo -u 1000 sysops \
&&  echo 'sysops:sysops' | chpasswd \
&&  mkdir -p /home/sysops \
&&  chown -R 1000:1000 /home/sysops

RUN apt update && apt upgrade -y \
&&  DEBIAN_FRONTEND=noninteractive \
&&  apt install -y apt --no-install-recommends openssh-server python \
&&  sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config \
&&  echo 'root:toor' | chpasswd \
&&  mkdir /run/sshd \
&&  apt clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* 

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
