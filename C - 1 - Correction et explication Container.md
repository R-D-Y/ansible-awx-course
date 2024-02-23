### Correction et Explication des Exercices

#### Correction de l'Exercice 1
1. **Commande à exécuter**:
   ```bash
   docker ps
   ```
2. **Explication**:
   - `docker ps`: Cette commande affiche les conteneurs actuellement en cours d'exécution. Pour voir tous les conteneurs, y compris ceux qui sont arrêtés, vous pouvez utiliser `docker ps -a`.

----------------------

#### Correction de l'Exercice 2
1. **Commande à exécuter**:
   ```bash
   docker run -it ubuntu
   ```
2. **Explication**:
   - `docker run -it ubuntu`: Cela démarre un nouveau conteneur basé sur l'image Ubuntu avec un terminal interactif. Une fois à l'intérieur, vous pouvez exécuter diverses commandes comme `ls` et `pwd`. Pour quitter le conteneur, tapez simplement `exit`.

----------------------

#### Correction de l'Exercice 3
1. **Commande à exécuter**:
   ```bash
   docker run -d -p 80:80 --name mon_apache httpd
   ```
   Puis, pour exécuter la commande `ls`:
   ```bash
   docker exec mon_apache ls
   ```
   Pour ouvrir un shell interactif:
   ```bash
   docker exec -it mon_apache /bin/bash
   ```
2. **Explication**:
   - La première commande exécute un conteneur Apache en arrière-plan et mape le port 80 du conteneur au port 80 de la machine hôte.
   - `docker exec`: Permet d'exécuter une commande à l'intérieur d'un conteneur en cours d'exécution.

----------------------

#### Correction de l'Exercice 4
1. **Commande à exécuter**:
   ```bash
   docker run -e MYSQL_ROOT_PASSWORD=password -d mysql
   ```
   Pour vérifier l'état:
   ```bash
   docker ps
   ```
   Pour arrêter et supprimer le conteneur:
   ```bash
   docker stop <ID_du_conteneur>
   docker rm <ID_du_conteneur>
   ```
2. **Explication**:
   - Cette commande démarre un conteneur MySQL en arrière-plan avec un mot de passe défini pour l'utilisateur root.

----------------------

#### Correction de l'Exercice 5

L'objectif de cet exercice est de comprendre comment lier des volumes avec Docker.

1. **Création d'un répertoire sur le système hôte**:
   ```bash
   mkdir /mon/repertoire
   ```

2. **Exécution du conteneur MySQL en liant le répertoire**:
   ```bash
   docker run -e MYSQL_ROOT_PASSWORD=password -d -v /mon/repertoire:/var/lib/mysql mysql
   ```

3. **Vérification des données MySQL**:
   Vous pouvez vérifier que les données MySQL sont stockées dans le répertoire `/mon/repertoire` sur votre système hôte.

4. **Arrêt et suppression du conteneur**:
   ```bash
   docker stop <ID_du_conteneur>
   docker rm <ID_du_conteneur>
   ```

5. **Recréation du conteneur avec le même répertoire lié**:
   ```bash
   docker run -e MYSQL_ROOT_PASSWORD=password -d -v /mon/repertoire:/var/lib/mysql mysql
   ```

6. **Vérification des données après la recréation du conteneur**:
   Vérifiez que les données sont toujours présentes dans le répertoire `/mon/repertoire` même après avoir supprimé et recréé le conteneur.
