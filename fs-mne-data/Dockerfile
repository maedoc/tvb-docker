FROM ubuntu:16.04
MAINTAINER Marmaduke Woodman <mmwoodman@gmail.com>

RUN apt-get update && apt-get install -y tcsh
WORKDIR /opt
ADD MNE*.tar.gz /opt/
ADD freesurfer*.tar.gz /opt/
ADD license.txt /opt/freesurfer/license.txt
