FROM ubuntu:latest

MAINTAINER jerivas@uaq.edu.mx

COPY download-kicad-library.sh /usr/local/bin/
COPY library-repos-install.sh /usr/local/bin/
COPY kicad-install.sh /usr/local/bin/

# Update the Ubuntu image to prevent it occuring below
RUN \
    apt-get update && \
    apt-get install -y software-properties-common && \
    add-apt-repository ppa:js-reynaud/ppa-kicad && \
    apt-get update && \
    apt-get upgrade -y && \
    add-apt-repository ppa:js-reynaud/ppa-kicad 

# Add the kicad user
RUN kicad-install.sh --install-or-update
RUN library-repos-install.sh  --install-prerequisites
RUN library-repos-install.sh  --install-or-update

RUN adduser --disabled-password --gecos "" kicad
USER kicad
# Download the .pretty component libraries




#ENV KISYSMOD /home/kicad/kicad_sources/library-repos
#
# Configuration and start up
VOLUME ["/home/kicad/projects", "/home/kicad/.kicad"]
WORKDIR /home/kicad/
# ENTRYPOINT ["kicad"]


