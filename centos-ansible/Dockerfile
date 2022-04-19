FROM centos:7
LABEL maintainer "Adiraju Havish Venkata Krishna Mouli havish.moulih@gmail.com"

RUN groupadd sysops \
&&  useradd -c "ansible-user" -d /home/sysops -s /bin/bash -g sysops -G wheel -u 1000 sysops \
&&  echo 'sysops:sysops' | chpasswd \
&&  mkdir -p /home/sysops \
&&  chown -R sysops:sysops /home/sysops

RUN yum update -y \
&&  yum install -y openssh-server python \
&&  yum clean all \
&&  sed -i 's/#PermitRootLogin yes/PermitRootLogin yes/' /etc/ssh/sshd_config \
&&  echo 'root:toor' | chpasswd \
&&  mkdir /run/sshd \
&&  ssh-keygen -A

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]

