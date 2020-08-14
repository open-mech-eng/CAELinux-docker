FROM docker.pkg.github.com/open-mech-eng/caelinux-docker/2020:1.0.0

RUN mv /etc/apt/sources.list /etc/apt/sources.list.bak 
RUN sed '/cdrom:\[CAElinux2020/ d' /etc/apt/sources.list.bak > /etc/apt/sources.list
RUN apt update
RUN apt install tightvncserver
RUN useradd caelinuxuser
USER vncserver

CMD [ "/bin/bash" ]
