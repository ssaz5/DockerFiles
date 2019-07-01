FROM ubuntu:16.04
# Updating Ubuntu packages
RUN apt-get update && yes|apt-get upgrade
RUN apt-get install -y emacs
# Adding wget and bzip2
RUN apt-get install -y wget bzip2 vim screen \
    && apt-get install -yq locales \
    && export LC_ALL="en_US.UTF-8" \
    && export LC_CTYPE="en_US.UTF-8" \
    && dpkg-reconfigure locales \
    && apt update && apt install -y libsm6 libxext6 libxrender-dev \
    && rm -rf ~/.cache/pip/* 
# Add sudo
RUN apt-get -y install sudo
# Add user ubuntu with no password, add to sudo group
RUN adduser --disabled-password --gecos '' suleman
RUN adduser suleman sudo
RUN echo '%sudo ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers
USER suleman
WORKDIR /home/suleman/
RUN chmod a+rwx /home/suleman/
#RUN echo `pwd`
RUN wget https://repo.anaconda.com/archive/Anaconda3-2019.03-Linux-x86_64.sh \
	 && bash ./Anaconda3-2019.03-Linux-x86_64.sh -b -p $HOME/anaconda
ENV PATH /home/suleman/anaconda/bin:$PATH
# Updating Anaconda packages
#RUN conda update conda
#RUN conda update anaconda
#RUN conda update --all
RUN conda install tensorflow-gpu=1.12.0 -y && conda install keras -y \
	 && conda install cudatoolkit=9.0 -y
LABEL maintainer="Syed Suleman Abbas Zaidi <ssazaidi@mit.edu>"
