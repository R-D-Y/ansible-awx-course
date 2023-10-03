
### Exercice 1
#### Objectif :
Familiarisation avec la commande `docker ps`.

#### Tâche :
1. Exécutez la commande `docker ps` sur votre terminal.
2. Analysez la sortie et identifiez les conteneurs en cours d'exécution.
3. Utilisez d'autres options de `docker ps` pour afficher différentes informations sur les conteneurs.

### Exercice 2
#### Objectif :
Apprentissage de la commande `docker run` pour démarrer un nouveau conteneur.

#### Tâche :
1. Exécutez un conteneur Ubuntu en utilisant `docker run -it ubuntu`.
2. À l'intérieur du conteneur, exécutez quelques commandes de base comme `ls`, `pwd`, etc.
3. Fermez le conteneur en utilisant `exit`.

### Exercice 3
#### Objectif :
Comprendre l'utilisation de la commande `docker exec` pour exécuter des commandes dans un conteneur en cours d'exécution.

#### Tâche :
1. Exécutez un conteneur en utilisant `docker run -d -p 80:80 --name mon_apache httpd`.
2. Utilisez `docker exec` pour exécuter la commande `ls` dans ce conteneur.
3. Utilisez `docker exec -it` pour ouvrir un shell interactif à l'intérieur du conteneur.

### Exercice 4
#### Objectif :
Pratique des différentes options de `docker run`.

#### Tâche :
1. Exécutez un conteneur MySQL en utilisant `docker run -e MYSQL_ROOT_PASSWORD=password -d mysql`.
2. Vérifiez l'état du conteneur avec `docker ps`.
3. Arrêtez et supprimez le conteneur en utilisant `docker stop` et `docker rm`.

### Exercice 5
#### Objectif :
Comprendre comment lier des volumes avec Docker.

#### Tâche :
1. Créez un répertoire sur votre système hôte, par exemple : `/mon/repertoire`.
2. Exécutez un conteneur MySQL tout en liant ce répertoire à `/var/lib/mysql` à l'intérieur du conteneur en utilisant `docker run -e MYSQL_ROOT_PASSWORD=password -d -v /mon/repertoire:/var/lib/mysql mysql`.
3. Vérifiez que les données MySQL sont stockées dans ce répertoire sur votre système hôte.
4. Arrêtez et supprimez le conteneur, puis recréez-le en utilisant le même répertoire lié.
5. Vérifiez que les données sont toujours présentes même après avoir supprimé et recréé le conteneur.


