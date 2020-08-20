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

# Install OpenFOAM and ParaView
RUN sh -c "wget -O - https://dl.openfoam.org/gpg.key | apt-key add -"
RUN add-apt-repository http://dl.openfoam.org/ubuntu
RUN apt-get update
RUN apt-get -y install openfoam8
RUN printf "source /opt/openfoam8/etc/bashrc" >> /headless/.bash_profile
# Install Salome Meca
# RUN wget https://code-aster.org/IMG/zip/sm2019_ubuntu18_install.sh.zip -O /tmp/sm2019_ubuntu18_install.sh.zip
# RUN cd /tmp
# RUN unzip ./sm2019_ubuntu18_install.sh.zip
# RUN chmod +x sm2019_ubuntu18_install.sh && sm2019_ubuntu18_install.sh
## switch back to default user
USER 1000
RUN printf "printf \"source ~/.bash_profile\" >> ~/.bashrc" >> ~/Desktop/load_envs.sh
RUN chmod a+x ~/Desktop/load_envs.sh
# RUN printf "[[ -s \"/opt/openfoam8/etc/bashrc\" ]] && source \"/opt/openfoam8/etc/bashrc\" \n" >> ~/.bashrc
