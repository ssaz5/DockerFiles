FROM ssazaidi/gcloud-repo:latest
# Updating Ubuntu package
RUN pip install imgaug 
RUN sudo apt-get install git -y
RUN pip install git+https://github.com/qubvel/classification_models.git
RUN sudo chmod u+s /usr/bin/screen
RUN sudo chmod 777 /var/run/screen
LABEL maintainer="Syed Suleman Abbas Zaidi <ssazaidi@mit.edu>"

