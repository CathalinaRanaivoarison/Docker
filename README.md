# Docker
[# student-list 
Ce dépôt est une application simple pour répertorier les étudiants avec un serveur web (PHP) et une API (Flask)

!\[project\](https://user-images.githubusercontent.com/18481009/84582395-ba230b00-adeb-11ea-9453-22ed1be7e268.jpg)


------------


## Objectifs

L'objectifs de ce projet est de gérer une infrastructure Docker.

### Themes:

- Améliorer un processus de déploiement d’application existant
- Gestion des versions de votre version d’infrastructure
- Aborder les meilleures pratiques lors de la mise en œuvre de l’infrastructure Docker
- Infrastructure As Code

## Context


*POZOS*  est une société informatique située en France et développe des logiciels pour le lycée.

Le département de l’innovation veut perturber l’infrastructure existante pour s’assurer que

Il peut être évolutif, facilement déployé avec un maximum d’automatisation.

POZOS souhaite construire un « POC » pour montrer comment docker peut  aider et à quel point cette technologie est efficace.

Pour ce POC, POZOS donnera une application et voudra que je construis une infrastructure « découple » basée sur « Docker ».

Actuellement, l’application s’exécute sur un seul serveur avec une évolutivité et une haute disponibilité.

Lorsque POZOS a besoin de déployer une nouvelle version, à chaque fois, certaines tournent mal.

En conclusion, POZOS a besoin d’agilité sur sa ferme logicielle.

## Infrastructure

Pour ce POC,  j’utiliserais qu’une seule machine sur laquelle un docker est installé.

La construction et le déploiement seront effectués sur cette machine.

POZOS recommande d’utiliser le système d’exploitation centos7.6 car c’est le plus utilisé dans l’entreprise.

## Application


L’application sur laquelle je vais travailler s’appelle « student_list », cette application est très basique et permet à POZOS d’afficher la liste des élèves avec leur âge.

student_list comporte deux modules :

- le premier module est une API REST (avec authentification de base nécessaire) qui envoie la liste de souhaits de l’étudiant basée sur un fichier JSON
- Le deuxième module est une application web écrite en HTML + PHP qui permet à l’utilisateur final d’obtenir une liste d’étudiants

Le travail consiste à construire un conteneur pour chaque module et à les faire interagir les uns avec les autres

Le code source de l’application peut être trouvé \[ici\](https://github.com/diranetafen/student-list.git "here")

Explication du rôle de chaque fichier:

- docker-compose.yml: pour lancer l’application (API et application web)
- Dockerfile:  le fichier qui sera utilisé pour construire l’image de l’API 
- requirements.txt: contient tous les packages à installer pour exécuter l’application
- student_age.json: contient le nom de l’élève avec l’âge au format JSON
- student_age.py: contient le code source de l’API en python
- index.php: Page PHP où l’utilisateur final sera connecté pour interagir avec le service afin de lister les étudiants par âge.
- docker-compose-registry.yml: pour lancer le registre local afin d’enregistrer l'API

```bash 
 $url = 'http://<api_ip_or_name:port>/pozos/api/v1.0/get_student_ages';
 ```



