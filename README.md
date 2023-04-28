# 20210149
TP1

THEIVENDIRAN Thushanthy


Pour la réalisation du TP1, voici les étapes que j'ai suivi : 

1) Création de 2 comptes : API Weather et Docker Hub

2) Installation de Docker sur ma machine virtuelle

3) Ecriture d'un code Python qui récupère les variables d'environnement LAT (latitude), LONG (longitude) et API_KEY (API Key associé au compte API OpenWeather) et renvoie, sous format JSON, le corps de la réponse de la réquête API. Utilisation, pour cela, des bibliothèques os et requests de Python, ce qui permet d'écrire un code concis.

4) Création d'un repository sur Docker Hub

5) Création d'un répertoire avec un DockerFile. Avec ce Dockerfile: 
- on crée une nouvelle image à partir de l'image Python 3.9 Alpine disponible sur Docker Hub
- on spécifie que l'on souhaite exécuter la commande "pip install requests" quand on déploie l'image, celle-ci étant nécessaire à l'exécution de notre code Python
- on crée les variables d'environnements nécessaire à l'exécution de la requête HTTP vers l'API Open Weather : LAT, LONG, API_KEY
- avec "COPY . ." on copie tous les fichiers du répertoire actuel vers le répertoire de travail /app dans l'image Docker afin d'inclure tous les fichiers nécessaires à l'exécution de l'application
- on exécute le fichier "TP1.py" avec python

6) On ouvre un terminal dans le répertoire avec le Dockerfile et on exécute les commandes suivantes afin de packager le code dans une image Docker (dockertp1:0.0.6 pour la version 6) et le mettre  à disposition sur DockerHub dans le repository créé précédemment (thushanthy/tp1) : 
- sudo docker build . -t dockertp1:0.0.6
- sudo docker tag dockertp1:0.0.6 thushanthy/tp1:0.0.6
- sudo docker push thushanthy/tp1:0.0.6


7) Dans un autre répertoire, on exécute la commande suivante pour récupérer l'image qui a été push dans notre répertoire : 
- sudo docker pull thushanthy/tp1:0.0.6

8) On vérifie que le tout fonctionne avec la commande : 
sudo docker run --env LAT="31.24" --env LONG="-99.5" --env API_KEY=**** thushanthy/tp1:0.0.6
