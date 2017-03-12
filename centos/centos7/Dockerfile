FROM centos:centos7
MAINTAINER Aurore <code@support.aurore.me>

RUN yum -y update && yum clean all

RUN yum -y install openssh-server && yum clean all

RUN mkdir /var/run/sshd

RUN ssh-keygen -t rsa -f /etc/ssh/ssh_host_rsa_key -N '' 

RUN sed -i 's/#UsePrivilegeSeparation.*/UsePrivilegeSeparation no/' /etc/ssh/sshd_config && \
    sed -i 's/session\s*required\s*pam_loginuid.so/session optional pam_loginuid.so/' /etc/pam.d/sshd

RUN echo 'root:admin' | chpasswd

EXPOSE 22

ENTRYPOINT ["/usr/sbin/sshd", "-D"]
