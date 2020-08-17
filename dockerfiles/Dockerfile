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

# Install SDKMAN, ANT AND JAVA
RUN apt-get -q -y install \
    curl \
    unzip \
    zip
RUN curl -s https://get.sdkman.io | bash
RUN chmod a+x "$HOME/.sdkman/bin/sdkman-init.sh"
RUN /bin/bash -c 'source $HOME/.sdkman/bin/sdkman-init.sh \
    && sdk install java 11.0.8.j9-adpt \
    && sdk install ant'
# Install Salome Meca
# RUN wget https://code-aster.org/IMG/zip/sm2019_ubuntu18_install.sh.zip -O /tmp/sm2019_ubuntu18_install.sh.zip
# RUN cd /tmp
# RUN unzip ./sm2019_ubuntu18_install.sh.zip
# RUN chmod +x sm2019_ubuntu18_install.sh && sm2019_ubuntu18_install.sh
## switch back to default user
USER 1000
