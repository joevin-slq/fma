# Image de base
FROM python:3

# Rends le port 80 accessible vers l'extérieur
EXPOSE 8888

# Définition de l'environement
WORKDIR /root
ENV PYENV_ROOT /root/.pyenv
ENV PATH /root/.pyenv/bin:/usr/local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

# Mise à jour des dépôts et installation d'unzip
RUN apt-get update && apt-get install unzip ffmpeg

# Installation de pyenv
RUN curl -L https://raw.githubusercontent.com/yyuu/pyenv-installer/master/bin/pyenv-installer | bash
RUN eval "$(pyenv init -)" && eval "$(pyenv virtualenv-init -)"

# Récupère le code de FMA
RUN git clone https://github.com/mdeff/fma.git && cd fma && git checkout rc1

# Récupère les données
RUN curl -O https://os.unil.cloud.switch.ch/fma/fma_metadata.zip && unzip fma_metadata.zip -d fma && rm fma_metadata.zip

# Installe l'environnement
RUN pyenv install 3.6.0		&& \
pyenv virtualenv 3.6.0 fma  && \
cd fma 						&& \
eval "$(pyenv init -)" &&		  \
eval "$(pyenv virtualenv-init -)" \
pyenv activate fma

# Désactive le mode GPU
RUN cd fma && \
eval "$(pyenv init -)" &&		  \
eval "$(pyenv virtualenv-init -)" && \
pyenv activate fma && \
sed -i -e 's/#tensorflow/tensorflow/g' requirements.txt			&& \
sed -i -e 's/tensorflow-gpu/#tensorflow-gpu/g' requirements.txt && \
make install

# Commandes de démarrage
ADD init.sh /root/fma/init.sh
RUN chmod +x /root/fma/init.sh

# Démarre jupyter en arrière plan
CMD ["/bin/bash", "-c", "/root/fma/init.sh"]

# docker build -t fma .
# docker run --name=fma -d -p 8888:8888 fma

# docker container exec -i -t fma /bin/bash