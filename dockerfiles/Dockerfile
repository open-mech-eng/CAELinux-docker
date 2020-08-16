FROM docker.pkg.github.com/open-mech-eng/docker-headless-vnc-container/ubuntu-xfce-vnc:1.0.0

# Switch to root user to install additional software
USER 0

# Enable PPAs
RUN apt update
RUN apt -y install software-properties-common dirmngr apt-transport-https lsb-release ca-certificates

# Install FREECAD
RUN add-apt-repository ppa:freecad-maintainers/freecad-stable
RUN apt update
RUN apt install --yes freecad
## switch back to default user
USER 1000
