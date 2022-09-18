FROM ubuntu:20.04
ENV DEBIAN_FRONTEND=noninteractive 
RUN apt-get update && apt-get -y install python3
RUN apt-get -y install -y build-essential python3-pip libffi-dev python3-dev python3-setuptools libssl-dev
RUN pip3 install flask
RUN apt-get install -y openssh-server
RUN mkdir /var/run/sshd
RUN echo 'root:root' | chpasswd
RUN sed -i'' -e's/^#PermitRootLogin prohibit-password$/PermitRootLogin yes/' /etc/ssh/sshd_config \
        && sed -i'' -e's/^#PasswordAuthentication yes$/PasswordAuthentication yes/' /etc/ssh/sshd_config \
        && sed -i'' -e's/^#PermitEmptyPasswords no$/PermitEmptyPasswords yes/' /etc/ssh/sshd_config \
        && sed -i'' -e's/^UsePAM yes/UsePAM no/' /etc/ssh/sshd_config
EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
