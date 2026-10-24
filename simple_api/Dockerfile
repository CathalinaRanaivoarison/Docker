FROM python:3.13-slim

LABEL maintainer="Cathalina <rnvscathalina22@gmail.com>"

# Paquets système nécessaires à la compilation de python-ldap (flask-simpleldap)
# - python-dev n'existe plus sur Debian récent : seul python3-dev est gardé
# - gcc est indispensable : l'image slim ne contient pas de compilateur
RUN apt update -y && \
    apt install -y gcc python3-dev libsasl2-dev libldap2-dev libssl-dev && \
    rm -rf /var/lib/apt/lists/*

# Dépendances Python
COPY requirements.txt /requirements.txt
RUN pip3 install --no-cache-dir -r /requirements.txt

# Code source de l'API à la racine
COPY student_age.py /student_age.py

# Dossier des données, déclaré comme volume
RUN mkdir /data
VOLUME /data

# Port de l'API Flask
EXPOSE 5000

# Se placer à la racine, là où se trouve student_age.py
WORKDIR /
CMD [ "python3", "./student_age.py" ]