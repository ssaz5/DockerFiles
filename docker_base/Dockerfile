FROM ubuntu:16.04
# Updating Ubuntu packages
RUN apt-get update && yes|apt-get upgrade
RUN apt-get install -y emacs
# Adding wget and bzip2
RUN apt-get install -y wget bzip2 vim
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
RUN conda update conda
RUN conda update anaconda
RUN conda update --all
RUN conda install tensorflow-gpu -y && conda install keras -y \


WORKDIR /home/suleman
LABEL maintainer="Syed Suleman Abbas Zaidi <ssazaidi@mit.edu>"

