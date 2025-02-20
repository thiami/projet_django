<p align="center">
    <img src="https://upload.wikimedia.org/wikipedia/fr/thumb/1/1d/Logo_T%C3%A9l%C3%A9com_SudParis.svg/153px-Logo_T%C3%A9l%C3%A9com_SudParis.svg.png" alt="TSP logo">
</p>


# CSC 8567 - Architectures distribuées et applications web

Auteurs : Timothée Mathubert, Gatien Roujanski, Arthur Jovart

## Emails

Lorsque vous envoyez un mail, pensez bien à mettre "CSC 8567" au début de l'objet !
- timothee.mathubert@telecom-sudparis.eu
- gatien.roujanski@telecom-sudparis.eu
- arthur.jovart@telecom-sudparis.eu

## Consignes

1. **Allez avant tout à la rubrique "Installation" ci-dessous pour installer ce dont vous aurez besoin pour le cours !**

2. Formez des groupes en trinômes, les plus hétérogènes possibles en niveau, et communiquez votre groupe à un enseignant.

3. **Ce cours est exclusivement un cours-projet : il n'y aura pas d'examen à la fin.** En revanche, il y aura deux rendus de projet (24 septembre et 21 novembre) ainsi qu'une soutenance à la fin du cours (21 novembre).

4. Vous pouvez faire le projet que vous souhaitez sous certaines conditions :
- **Vous devez disposer de deux applications Django**, une pour **un frontend** et l'autre pour **une API retournant des données au format JSON**. 
- Votre site web doit être accessible depuis votre interface loopback (sur l'IP 127.0.0.1) de votre PC, et contenir au moins deux pages : une pour faire des requêtes à l'API, l'autre pour afficher une liste d'objets.
- **Votre site doit utiliser une base de données non locale (pas de fichier).** Celle-ci doit contenir un schéma relationnel de données similaire à celui ci-dessous :

<p align="center">
    <img src="https://github.com/user-attachments/assets/4cd224f5-5f64-48b7-bd6f-c25f301275ca" alt="BDD">
</p>

- Pour le rendu du 24 septembre, vous devez déployer une infrastructure similaire à celle ci-dessous en utilisant un fichier `docker-compose.yml` et des Dockerfiles. **L'application Django de l'API et du frontend devront être placées dans deux conteneurs différents. La base de données et le proxy seront dans deux conteneurs différents.**

<p align="center">
    <img src="https://github.com/user-attachments/assets/877dfc8f-ae0b-41e0-a934-19480d839d0c" alt="Infra à reproduire">
</p>

- Pour vous aider tout au long du projet, __**consultez ces différentes pages de documentation et demandez de l'aide aux enseignants**__ :
    - Django : https://docs.djangoproject.com/en/5.1/
    - Docker : https://docs.docker.com/manuals/ 
    - Kubernetes (rendu final seulement) : https://kubernetes.io/fr/docs/home/
    - Nginx (Proxy) : https://nginx.org/en/docs/
- *Vous pouvez ajouter des applications, ajouter de la forme (Styles CSS, Bootstrap, Bulma) et des pages supplémentaires si vous le souhaitez.*
- Les consignes pour le rendu final avec Kubernetes vous seront communiquées après le rendu du CC Django + Docker.


## Installation

**Il est recommandé d'utiliser un système d'exploitation type Linux.**
L'installation suivante fonctionne sous Ubuntu. En fonction de votre OS, il est possible qu'apt ne soit pas le gestionnaire de paquets. Remplacez simplement apt dans les commandes suivantes par votre gestionnaire de paquets.

1. Créez votre propre répo de groupe en cliquant sur "Use this template"
   
2. Créer un environnement virtuel Python avec Pyenv (non nécessaire si vous avez déjà un gestionnaires d'environnements virtuels pour Python)
```
sudo apt install pyenv
sudo apt install python
sudo apt install pip
```
Si vous utilisez Bash comme exécuteur de commande dans votre Shell :
```
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc
echo 'command -v pyenv >/dev/null || export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(pyenv init -)"' >> ~/.bashrc
```
Si vous utilisez autre chose, allez voir la [documentation Pyenv](https://github.com/pyenv/pyenv?tab=readme-ov-file#set-up-your-shell-environment-for-pyenv).

Ensuite :
```
pyenv install 3.12
```
3. Installer les dépendances utiles
```
pip install django psycopg2-binary
```
4. Créer le projet Django & vérifier qu'il tourne correctement
```
cd django-site
django-admin startproject [nom-de-votre-projet] <-- A REMPLACER
python manage.py runserver
```
Allez sur 127.0.0.1:8000 sur un navigateur. Si une page "Congratulations!" s'affiche, c'est que tout fonctionne bien !

5. Créer les applications utiles
```
python manage.py startapp public
python manage.py startapp api
```

6. Installer Docker
```
sudo apt install docker
docker -v
```
Si la dernière commande vous affiche la version de Docker, c'est qu'il est correctement installé.

7. Créer un compte Docker Hub

Allez sur https://hub.docker.com et créez vous un compte.

8. Installer kubectl
```
sudo apt install kubectl
```

Et c'est parti !
