FROM ubuntu:14.04
MAINTAINER Kiran <skyrus@gmail.com>

RUN apt-get update 

RUN apt-get install -y build-essential  

RUN apt-get install -y cmake git libgtk2.0-dev pkg-config && \
    apt-get install -y libavcodec-dev libavformat-dev libswscale-dev 

RUN apt-get install -y python-dev python-numpy && \
    apt-get install -y libtbb2 libtbb-dev && \
    apt-get install -y libjpeg-dev libpng-dev libtiff-dev libjasper-dev && \ 
    apt-get install -y libdc1394-22-dev

RUN apt-get install -y wget && \ 
    apt-get install -y vim

RUN apt-get install -y libglib2.0-0 && \
    apt-get install -y libxext6 && \
    apt-get install -y libsm6 && \
    apt-get install -y libxrender1 

# install qt
RUN apt-get install qtcreator -y

ENV HOME /home/opencv

RUN useradd --create-home --home-dir $HOME --shell /bin/bash opencv

# make opencv user a sudoer
RUN chmod +w /etc/sudoers && \
    echo "opencv   ALL=(ALL)       NOPASSWD:ALL" >> /etc/sudoers && \
    chmod -w /etc/sudoers 

# install miniconda
RUN \
    mkdir $HOME/Downloads && \
    cd $HOME/Downloads && \
    wget --quiet https://repo.continuum.io/miniconda/Miniconda-latest-Linux-x86_64.sh && \
    bash Miniconda-latest-Linux-x86_64.sh -b  && \ 
    echo "PATH=$HOME/miniconda2/bin:$PATH" >> ~/.bashrc 

COPY environment.yml $HOME/Downloads/environment.yml

RUN cd $HOME/Downloads/ && \
    $HOME/miniconda2/bin/conda env create 

# clone opencv
RUN \ 
    mkdir $HOME/opencv && \
    cd $HOME/opencv && \
    git clone https://github.com/Itseez/opencv.git && \
    git clone https://github.com/Itseez/opencv_contrib.git

RUN chown -R opencv:opencv $HOME
