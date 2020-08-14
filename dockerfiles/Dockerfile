FROM docker.pkg.github.com/open-mech-eng/caelinux-docker/2020:1.0.0

RUN mv /etc/apt/sources.list /etc/apt/sources.list.bak 
RUN sed '/cdrom:\[CAElinux2020/ d' /etc/apt/sources.list.bak > /etc/apt/sources.list
RUN apt update
RUN apt install --yes tightvncserver

RUN useradd caelinuxuser && mkdir /home/caelinuxuser
RUN chown -R caelinuxuser:caelinuxuser /home/caelinuxuser
USER caelinuxuser
ENV USER=caelinuxuser

WORKDIR /home/caelinuxuser
CMD [ "/bin/bash" ]
