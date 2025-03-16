# Student List - Dockerized Application

## 📝 Description
Ce projet consiste à dockeriser une application simple qui affiche une liste d'étudiants avec leur âge. L'application est constituée de deux modules :
- Une API Flask qui renvoie la liste des étudiants sous forme de JSON.
- Une interface Web PHP permettant aux utilisateurs d'interagir avec l'API pour afficher les étudiants.

  ![image](https://github.com/user-attachments/assets/1ddc4468-e6eb-44fe-addb-3a20e181f0d5)


L'objectif de ce projet est de démontrer la gestion d'une infrastructure Docker et de mettre en place des bonnes pratiques DevOps, telles que l'automatisation, la séparation des responsabilités, et l'utilisation de Docker pour déployer l'application de manière scalable et fiable.

## 🚀 Objectifs de l'exercice
- Améliorer le processus de déploiement d’une application existante.
- Versionner l'infrastructure.
- Appliquer les meilleures pratiques lors de la mise en œuvre de l’infrastructure Docker.
- Utiliser Infrastructure as Code pour la gestion des conteneurs.

## ⚙️ Technologies utilisées
- **Docker & Docker Compose** : Orchestration des conteneurs.
- **Flask (Python)** : Framework utilisé pour l’API.
- **PHP (Apache)** : Framework utilisé pour l’application Web.
- **CentOS 7.6** : Système d’exploitation utilisé pour le POC.
- **Docker Registry** : Pour stocker les images Docker.

## 📂 Structure du répertoire


## 🚀 Instructions de déploiement
1. **Cloner le dépôt** :

    ```bash
    git clone https://github.com/ton-compte/student-list.git
    cd student-list
    ```

2. **Construire l'image Docker pour l'API** : Dans le fichier `Dockerfile`, l’image sera construite avec la commande suivante :

    ```bash
    docker build -t student-api .
    ```

3. **Lancer les services avec Docker Compose** : Utilise `docker-compose` pour déployer l’application (API et Web) :

    ```bash
    docker-compose up -d
    ```

4. **Accéder à l'application** :

    - API : [http://localhost:5000/pozos/api/v1.0/get_student_ages](http://localhost:5000/pozos/api/v1.0/get_student_ages)
    - Web : [http://localhost:80](http://localhost:80)

5. **Test de l’API** : Pour tester si l'API fonctionne correctement, utilise la commande `curl` :

    ```bash
    curl -u toto:python -X GET http://localhost:5000/pozos/api/v1.0/get_student_ages
    ```

6. **Docker Registry** : Déployer un Docker Registry local pour stocker les images :

    ```bash
    docker run -d -p 5000:5000 --name registry registry:2
    ```

    Puis pousser l'image API dans le registre :

    ```bash
    docker tag student-api localhost:5000/student-api
    docker push localhost:5000/student-api
    ```

## 🔧 Explications de la mise en œuvre
- **Dockerfile** : Ce fichier contient les instructions pour créer l'image de l'API Flask. Il inclut l'installation des dépendances et la mise en place du volume de données.
  
- **docker-compose.yml** : Ce fichier permet d’orchestrer les deux services (API et Web). Il spécifie les configurations pour les conteneurs, y compris les volumes, les ports, et les dépendances entre les services.

- **Docker Registry** : Un registre privé est mis en place pour stocker et partager les images Docker créées.

## 📸 Captures d'écran
- **Image 1** : Capture d'écran de l’interface Web avec la liste des étudiants.
- **Image 2** : Test de l’API avec `curl`.

## 🛠 Livraison
Ce projet est livré avec :
- Les fichiers de configuration (Dockerfile, docker-compose.yml).
- Le code source de l’application et de l'API.
- Un Docker Registry local avec l’image stockée.
