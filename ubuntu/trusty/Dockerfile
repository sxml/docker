FROM ubuntu:trusty
MAINTAINER Aurore <code@support.aurore.me>

RUN apt-get update && apt-get -y install --no-install-recommends openssh-server && rm -rf /var/lib/apt/lists/*

RUN mkdir /var/run/sshd

RUN sed -i 's/^PermitRootLogin.*/PermitRootLogin yes/' /etc/ssh/sshd_config && \
    sed -i 's/session\s*required\s*pam_loginuid.so/session optional pam_loginuid.so/' /etc/pam.d/sshd

RUN echo 'root:admin' | chpasswd

EXPOSE 22

ENTRYPOINT ["/usr/sbin/sshd", "-D"]
