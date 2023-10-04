### Correction et Explication des Exercices

#### Correction de l'Exercice 1
1. **Commande à exécuter**:
   ```bash
   docker run -d -p 80:80 nginx
   ```
2. **Explication**:
   - `docker run`: Commande pour exécuter un conteneur.
   - `-d`: Détache le conteneur du terminal, permettant de libérer le terminal tout en laissant le conteneur s'exécuter en arrière-plan.
   - `-p 80:80`: Fait correspondre le port 80 du système hôte avec le port 80 du conteneur, permettant d'accéder au serveur web du conteneur depuis le navigateur.

----------------------

#### Correction de l'Exercice 2
1. **Commande à exécuter**:
   ```bash
   docker ps -a
   ```
2. **Explication**:
   - `docker ps -a`: Affiche tous les conteneurs, y compris ceux qui ne sont pas en cours d'exécution.

----------------------

#### Correction de l'Exercice 3
1. **Commande à exécuter**:
   ```bash
   docker exec -it <ID_du_conteneur> /bin/bash
   ```
2. **Explication**:
   - `docker exec`: Exécute une commande à l'intérieur d'un conteneur en cours d'exécution.
   - `-it`: Permet une interaction interactive avec le terminal du conteneur.
   - `<ID_du_conteneur>`: Remplacez ceci par l'ID du conteneur que vous voulez accéder.
   - `/bin/bash`: Spécifie la commande à exécuter dans le conteneur, dans ce cas, le shell bash.

----------------------

#### Correction de l'Exercice 4
1. **Commande à exécuter**:
   ```bash
   docker run -e MYSQL_ROOT_PASSWORD=password -d -v /mon/repertoire:/var/lib/mysql mysql
   ```
2. **Explication**:
   - `-e MYSQL_ROOT_PASSWORD=password`: Définit un mot de passe pour l'utilisateur root de MySQL dans le conteneur.
   - `-d`: Détache le conteneur du terminal, permettant de libérer le terminal tout en laissant le conteneur s'exécuter en arrière-plan.
   - `-v /mon/repertoire:/var/lib/mysql`: Montre le répertoire `/mon/repertoire` du système hôte dans `/var/lib/mysql` du conteneur, permettant ainsi à MySQL de stocker ses données dans ce répertoire.

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

   - `-e MYSQL_ROOT_PASSWORD=password`: Définit un mot de passe pour l'utilisateur root de MySQL dans le conteneur.
   - `-d`: Détache le conteneur du terminal, permettant de libérer le terminal tout en laissant le conteneur s'exécuter en arrière-plan.
   - `-v /mon/repertoire:/var/lib/mysql`: Montre le répertoire `/mon/repertoire` du système hôte dans `/var/lib/mysql` du conteneur, permettant ainsi à MySQL de stocker ses données dans ce répertoire.

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

En liant un répertoire du système hôte au répertoire `/var/lib/mysql` du conteneur, nous permettons à MySQL de stocker ses données dans ce répertoire sur le système hôte. Cela garantit que les données persistent même si le conteneur est arrêté, supprimé et recréé.
