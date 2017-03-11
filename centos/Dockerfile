FROM centos:latest
MAINTAINER Aurore <code@support.aurore.me>

RUN yum makecache && \
    yum -y install openssh-server && \
    yum clean all

RUN mkdir /var/run/sshd

RUN ssh-keygen -q -N "" -t dsa -f /etc/ssh/ssh_host_ecdsa_key && \
    ssh-keygen -q -N "" -t rsa -f /etc/ssh/ssh_host_rsa_key

RUN sed -i 's/#UsePrivilegeSeparation.*/UsePrivilegeSeparation no/' /etc/ssh/sshd_config && \
    sed -i 's/session\s*required\s*pam_loginuid.so/session optional pam_loginuid.so/' /etc/pam.d/sshd

RUN echo 'root:admin' | chpasswd

EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]
