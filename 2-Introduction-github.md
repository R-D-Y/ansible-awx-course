   
# **[1] Introduction à GitHub**

---

#### **1. Qu'est-ce que GitHub?**

GitHub est une plateforme qui va permettre d'héberger, de partager et de collaborer sur des projets de code. Il s'agit de la plateformes la plus populaire pour le contrôle de versionning et la collaboration, permettant à plusieurs personnes de travailler ensemble sur des projets. (Pour information, et de façon Open-source, il existe Gitlab qui est un Github en locale permettant de retrouver cette aspect collaboratif, ainsi que Git, permettant de faire du versionning).

Il facilite la collaboration entre les développeurs. Grâce à ses fonctionnalités, comme les "pull requests" et les "issues", les équipes vont pouvoir travailler ensemble de manière plus efficace, ils pourront modifier le code de leurs compère en temps réel, émèttre des commentaires, validé ou non leurs mises en applications... mais nous y reviendrons !!!
Deplus, ils offrent un espace gratuit pour héberger tes dépôts de code, ce qui nous permet de sauvegarder et de partager nos projet, de façon publique ou privé. Enfin, Github s'intègre avec de nombreux outils et services, ou encore plugins comme des outils de CI/CD, pour automatiser et améliorer la productivité (certain produit son même directement conçu par GIthub comme Github-action qui permet de créer des workflows automatiquement).

---

#### **2. Pourquoi utiliser GitHub?**

Beaucoup raisons.... Mais les développeurs et les entreprises choisissent d'utiliser GitHub pour certaines d'entres-elles:

- **Collaboration en équipe**: GitHub va faciliter la collaboration en équipe en offrant des outils intégrés qui permettent aux développeurs de travailler ensemble, de discuter des modifications et de résoudre les problèmes, nous y reviendrons plus tard, mais tout est fait pour que ce soit un espace collaboratif.

- **Versionnage du code**: Avec GitHub, chaque modification du code est suivie, ce qui permet de voir qui a fait quoi et quand. ça facilite la détection des erreurs et la collaboration, nous pouvons ainsi remonter dans le temps à la modification `x` et la remettre en place ou non.

- **CI/CD**: Comme expliquer précédemment, Github permet entre-autre de faire de la CICD, permettant une meilleur productivité !! la CICD peut-être apporter par Github lui-même, avec les workflow github actions, ou bien via des applications tierces qui vont directemment aller questionner github en directe.

---

#### **3. Différence entre Git et GitHub**

- **Git**: C'est un système de contrôle de version distribué. Il permet de suivre les modifications du code réalisé, de créer des branches et de fusionner ces branches (branche production, branche préproduction par exemple). Git fonctionne localement sur l'ordinateur, à l'inverse de github qui est en SaaS.

- **GitHub**: C'est une plateforme basée sur Git qui propose en plus de  l'hébergement pour les dépôts Git. En plus des fonctionnalités de Git, GitHub offre aussi des outils pour la collaboration et l'intégration avec d'autres services.

---



![Introduction à GitHub](https://showme.redstarplugin.com/d/d:xXVm4JiG)

---


# **[2] Interface Graphique de GitHub**

---

#### **1. Présentation de l'interface utilisateur**

L'interface utilisateur de GitHub est conçue pour être intuitive et conviviale. Voici quelques éléments clés de l'interface:

- **Dashboard**: C'est la première page que tu vois lorsque tu te connecte à GitHub. Il affiche une vue d'ensemble des activités, des dépôts personnels, des dépôts que tu suis (stars), et plus encore.

![image](https://github.com/R-D-Y/ansible-awx-course/assets/102509252/92b4af8d-7618-472c-b36b-54778a6220c8)


- **Profil utilisateur**: Ton profil montre ta photo, ta biographie, et une liste de tes dépôts. Pour certains développeur, Github Agit comme un CV, il permet de montrer leurs projets.

![image](https://github.com/R-D-Y/ansible-awx-course/assets/102509252/ef0b3953-7a74-4acf-aa9c-f84dfe82e5a5)


- **Notifications**: Vous recevez des notifications pour les activités liées à vous ou aux dépôts que vous suivez, comme les issues et les pull requests.

![image](https://github.com/R-D-Y/ansible-awx-course/assets/102509252/8430428c-ff29-409a-be79-6a607c0f5a01)


- **Paramètres**: Dans les paramètres, tu peux configurer ton compte, gérer sa sécurité, tes clés SSH, et d'autres préférences.

![image](https://github.com/R-D-Y/ansible-awx-course/assets/102509252/f41e146f-ee1f-4597-ab2a-0684f85ed5e6)

- **Bonus: Statistique**: Vous pouvez visionnez, en bas de chaque compte Github, le taux de contribution de l'utilisateur, afin de voir si ceui-ci est actif ou non !

![image](https://github.com/R-D-Y/ansible-awx-course/assets/102509252/59d3eff8-49ad-4c1f-b6c2-194d51f65a67)


---

#### **2. Création d'un nouveau dépôt (repository)**

Créer un nouveau dépôt sur GitHub est un processus simple:

![image](https://github.com/R-D-Y/ansible-awx-course/assets/102509252/18e69b59-79b8-47a6-baba-8a7f3cc58cb3)


- **Choix du nom**: Choisissez un nom logique pour votre dépôt.

![image](https://github.com/R-D-Y/ansible-awx-course/assets/102509252/be46e8e6-98b2-4a7e-b4db-f2e7fce92359)

  
- **Description**: Ajoutez une brève description pour aider les autres users à comprendre le but de votre dépôt.

![image](https://github.com/R-D-Y/ansible-awx-course/assets/102509252/0495a8ae-f6a5-4a6f-aea0-5dcb0577c6d0)

  
- **Visibilité**: Vous pouvez choisir de rendre votre dépôt public (visible par tout le monde) ou privé (visible uniquement par vous et les personnes que vous invitez).

![image](https://github.com/R-D-Y/ansible-awx-course/assets/102509252/cff3d53b-12b7-4dc0-8265-5ef74e48f91f)

  
- **Initialisation avec README**: Il est recommandé d'initialiser votre dépôt avec un fichier README pour fournir des informations sur votre projet. Il va s'agir d'un fichier afficher par défaut dès que quelqu'un cliquera sur votre dépôt, il peut s'agir d'une description plus poussé, et de tutoriels relatif au projet que vous partager.

  ![image](https://github.com/R-D-Y/ansible-awx-course/assets/102509252/ef790dca-0bff-4694-802a-2cd34875ee8e)

- **Initialisation avec .gitignore**: Cela permettra d'exclure des fichiers inutiles pour l'utilisateur qui souhaite télécharger votre projet, si par exemple vous ne souhaitez pas qu'il télécharge votre readme, vous ajouter une exception pour l'exclure.

![image](https://github.com/R-D-Y/ansible-awx-course/assets/102509252/7b8b4ec5-b432-4431-9547-36d0dfe2fed1)


- **Initialisation avec Licence**: vous pouvez choisir de mettre une licence sur votre projet, afin d'autorisé ou non des choses que les utilisateurs pourraient faire avec votre code.

![image](https://github.com/R-D-Y/ansible-awx-course/assets/102509252/516b4ede-179c-495c-8637-4af87ef685f0)

  
---

#### **3. Clonage, fork et gestion des branches**

- **Clonage d'un dépôt**: Le clonage vous permet de copier un dépot votre machine locale afin d'avoir le code disponible sans web. Vous pouvez clonner de plusieurs manières en HTTPS, en SSH, en Github CLI, ou bien même avec le client lourd GithubDesktop, et enfin dans un fichier zippé.

  ![image](https://github.com/R-D-Y/ansible-awx-course/assets/102509252/8f87cdd7-df19-4c59-9b30-55089adfef80)


- **Forking**: Le forking crée une copie personnelle d'un dépôt d'une autre personne. Vous allez prendre le projet d'un tiers, l'apporter dans votre dépot personnel, potentiellement apporté des modifications dessus, puis après pouvoir faire un commit afin de repousser vos modifications sur le projet de la personne tierce.

  ![image](https://github.com/R-D-Y/ansible-awx-course/assets/102509252/1eee7052-1767-43e5-8574-07d840e15996)


- **Gestion des branches**: Les branches vous permettent de travailler sur différentes fonctionnalités ou corrections sans affecter la branche principale. Cela vous permet de créer des environnement de developpement afin de ne pas créer des débordements d'erreur, ainsi, vous pouvez traiter vos actions step by step sans risquer de compromettre certaines partie de votre code.

  ![image](https://github.com/R-D-Y/ansible-awx-course/assets/102509252/9c7ff4ef-c435-4caa-bb55-93880371bb00)

---

#### **4. Utilisation des issues et des pull requests**

- **Création d'une issue**: Les issues sont utilisées pour suivre les bugs, Si vous utiliser un projet sur github, et que vous vous rendez-compte d'un problème sur ce dernier, vous pouvez créer une issue, et expliquer votre problème au mainteneur, celui-ci, si il maintient toujours le projet, pourra la corriger, encore une fois, le collaboratif prend son sens, car des personnes tierce, ou vous-même pouvez proposer une correction au code.

  

![image](https://github.com/R-D-Y/ansible-awx-course/assets/102509252/78b630b2-84c4-4d67-a1c4-f8df4164fb7a)


- **Assignation et labels**: Travaillant à plusieurs sur un projet, si je reçois des issues, je vais pouvoir désigner qui doit s'en occuper afin de répartir les taches, et je vais aussi pouvoir tagger mes issues, si il s'agit d'un bug, d'une duplication d'une demande d'aide ou autre.
Par exemple, ci dessous, je vais attribuer l'issue à mon collègue Antoine en taggant celle-ci comme un bug, il recevra donc une notification et pourra commencer à travailler.

  ![image](https://github.com/R-D-Y/ansible-awx-course/assets/102509252/8fa681a2-c97c-4d0c-a09d-8cdf87cf5881)


- **Création d'une pull request**: Dans le cas ou j'ai terminé mon projet, mais que Antoine a travailler sur une nouvelle fonctionnalité, il avait créer une nouvelle branche, il a pu tester son code, il était donc fonctionnel, il demande maintenant a poussé sa nouvelle fonctionnalité en Production, il utilise pour cela un pull-request, il demande enfaite simplement de combiné son code à celui déja présent.

  ![image](https://github.com/R-D-Y/ansible-awx-course/assets/102509252/e28ea87c-2ed5-4c66-822e-7fe7b7fb98bc)


- **Review et merge de la pull request**: Une fois la pull request créée, les membres de moi-même ou Antoine peuvent la revoir, la commenter et, une fois approuvée, la fusionner avec la branche principale.

![image](https://github.com/R-D-Y/ansible-awx-course/assets/102509252/aa915aaa-9616-42ec-aaaa-5c8505945606)

![image](https://github.com/R-D-Y/ansible-awx-course/assets/102509252/af90a1d5-2bc3-4e19-8745-297c47a525eb)

---

Recapitulatif Interface graphique de GitHub:

![Interface Graphique de GitHub](https://showme.redstarplugin.com/d/d:9IXcmqzH)

---


# **[3] Ligne de Commande (CLI) avec Git et GitHub**

---

#### **1. Installation et configuration de Git**

Avant de commencer à utiliser Git et GitHub via la ligne de commande, Il faut commencer par l'installer en local !

**Installation**: Selon ton système d'exploitation (Windows, Linux), la procédure d'installation va varier. tu peux télécharger Git depuis le [site officiel de Git](https://git-scm.com/).

- **Configuration**: Une fois Git installé, configurer votre nom d'utilisateur et votre adresse e-mail github. elle permettrons de relier tes actions à ton compte.
  
  ```bash
  git config --global user.name "Votre Nom"
  git config --global user.email "votre.email@example.com"
  ```

---

#### **2. Commandes de base**

- **`git clone [URL]`**: Permet de cloner (copier) un dépôt depuis GitHub vers votre machine locale. Tu te retrouvera donc avec les fichiers/Dossier du projet

![image](https://github.com/R-D-Y/ansible-awx-course/assets/102509252/1f72d959-6e1a-4a27-aa55-e1ce19737ca3)


- **`git add [fichier]`**: Ajoutez des fichiers à l'index pour les préparer pour le prochain commit.

- **`git commit -m 'Message'`**: Créez un nouveau commit avec les fichiers ajoutés à l'index. Le message du commit doit décrire les modifications effectuées.

- **`git push`**: Envoyez vos commits vers le dépôt distant sur GitHub.

- **`git pull`**: Récupérez les dernières modifications du dépôt distant.

- **`git branch [nom]`**: Créez une nouvelle branche.

- **`git checkout [nom_branche]`**: Changez de branche pour travailler sur une fonctionnalité ou une correction spécifique.

---

#### **3. Création et gestion de dépôts via CLI**

- **`git init`**: Initialisez un nouveau dépôt Git, dans votre répertoire actuel. Cela crée un nouveau sous-répertoire `.git` qui contient tous les fichiers nécessaires pour le dépôt.

- **Ajout d'un dépôt distant**: Une fois que vous avez initialisé un dépôt local, vous pouvez le lier à un dépôt distant sur GitHub en utilisant la commande:
  ```bash
  git remote add origin [URL_du_dépôt_GitHub]
  ```

- **Push vers le dépôt distant**: Après avoir effectué vos commits localement, vous pouvez les envoyer vers le dépôt distant avec:
  ```bash
  git push -u origin master
  ```

---

Flux de travail avec Git et GitHub via la ligne de commande:

![Flux de travail avec Git et GitHub](https://showme.redstarplugin.com/d/d:1mwhlZ8L)

---

# **[4] Bonnes Pratiques sur GitHub**

---

#### **1. Nommage des dépôts et des branches**

Le nommage est important afin de mieux gérer les projets. Je te donne ici quelques tips!

- **Descriptif et concis** : Le nom doit refléter le contenu ou la fonction du dépôt/branche comme par exemple `maquette` pour dire que c'est la branche de maquette, ou encore par un nom de fonctionnalité que tu t'apprête à créer : branche `compteur-de-temps`.
  
- **Éviter les noms génériques** : Les noms comme "test" ou "nouveau" ne sont pas dutout informatifs. Optez pour des noms qui donnent un aperçu du contenu, sans aller dans la branche, vous devez avoir une idée de ce qu'elle contient.
  
- **Utiliser des tirets pour séparer les mots, et sans ponctuation, ni majuscules** : Comme, "documentation-awx" sera préférable à "documentationAWX" ou "Documentation_Awx".

---

#### **2. Utilisation des messages de commit descriptifs**

Un bon message de commit va faciliter la compréhension de l'historique du projet, et évidemment aider ton collègue qui passera derrière toi :

- **Commencer par un verbe d'action** : Par exemple, "Creation la fonctionnalité X" ou "Isolement du bug Y".

![image](https://github.com/R-D-Y/ansible-awx-course/assets/102509252/619a2a9d-d9db-42be-9cca-8838373bfa92)

  
- **Limiter à 50 caractères pour le titre** : Si vous avez besoin d'écrire plus de détails, privilégié le corps du message de commit. Fournissez des informations supplémentaires sur ce que fait le commit et pourquoi.

![image](https://github.com/R-D-Y/ansible-awx-course/assets/102509252/49a8f872-9f15-4504-95ca-f8506f3310dc)


---

#### **3. Gestion des branches**

La gestion efficace des branches est essentielle pour le bon développement d'un projet :

- **Feature branching** : Créez une branche pour chaque nouvelle fonctionnalité a ajouter ou modifier. Cela va permettre de travailler sur des éléments spécifiques sans perturber la branche principale qui est généralement la production.
  
- **Git flow** : C'est un modèle de workflow standardisé qui définit une structure de branches pour vos fonctionnalités, les corrections, les versions, etc. plus d'info ici > https://danielkummer.github.io/git-flow-cheatsheet/index.fr_FR.html
  
- **Ne jamais travailler directement sur la branche 'master'** : Comme expliqué précédemment, la branche 'master' doit toujours être stable et aucune opération ne dois être faite sur cette dernière. Donc je le répète, vous souhaité créer une nouvelle fonctionnalité, ou modifier la principale, créer une nouvelle branche, modifier, et pusher !! 
---

#### **4. Utilisation des labels et des milestones (TAG)**

Les labels et les milestones aident à organiser et à prioriser le travail :

- **Catégoriser les issues** : Utilisez des labels pour indiquer le type d'issue (bug, fonctionnalité, amélioration, etc.) cela doit permettre de savoir quelle type de tâche sera attribué au contributeur.
  
- **Prioriser les tâches** : Les milestones peuvent être utilisés pour regrouper des issues liées à une version ou à une étape spécifique du projet, par exemple, il y aura une priorité sur la correction d'un bug, plutôt que de créer une nouvelle fonctionnalité ! dans ce cas, vous pouvez priorisé certaines issues.
  
- **Suivre l'avancement du projet** : Les milestones fournissent une vue d'ensemble de l'avancement vers un objectif particulier, vous avez d'ailleur, sur Github, le mode projet qui va vous permettre d'avoir une vue d'ensemble sur l'avancement du projet, savoir qui doit faire quoi, ainsi que l'état d'avancement de ce dernier (tâche par tâche ou bien global au projet).

![image](https://github.com/R-D-Y/ansible-awx-course/assets/102509252/c5cb4094-5091-404d-a551-7b5a771f2902)


---

Les Bonnes pratiques sur GitHub :

![Bonnes Pratiques sur GitHub](https://showme.redstarplugin.com/d/d:ZxrF7C54)

---

# **[5] Sécurité et Clés SSH avec GitHub**

---

#### **1. Qu'est-ce qu'une clé SSH et pourquoi l'utiliser?**

SSH est un protocole qui permet d'établir une communication sécurisée entre deux systèmes. Dans le contexte de GitHub, les clés SSH sont utilisées pour établir une connexion sécurisée entre votre ordinateur local et GitHub, sans avoir besoin de saisir votre mot de passe à chaque fois, dans le cas de notre projet, Nous avons par exemple un échange de clé entre le VM_NODE et le VM_MASTER, afin que le master puisse réalisé des actions sur le NODE sans avoir a tapper de mot de passe. our information, le port SSH est le 22 ! mais vous devez le savoir ahah

![image](https://github.com/R-D-Y/ansible-awx-course/assets/102509252/c6e94d4f-e22a-4014-bfd5-c3e4e9fda5a0)


**Avantages de l'utilisation des clés SSH** :
- **Sécurité renforcée** : Les clés SSH offrent un niveau de sécurité plus élevé que les mots de passe simples, composé de beaucoup plus de caractère évidemment, ainsi qu'un count-retry qui permet de bloquer les tentatives de *brutforce*.
- **Authentification sans mot de passe** : Une fois la clé SSH configurée, vous n'avez pas besoin de saisir votre mot de passe à chaque fois que vous interagissez avec GitHub, le lien est réalisé par SSH qui vérifie la clé.
- **Automatisation** : Les clés SSH sont essentielles pour les scripts et les automatisations qui nécessitent des interactions fréquentes avec les dépôts, 99.99% sont effectuer comme cela :) .

---

#### **2. Génération et ajout d'une clé SSH à GitHub**

**Génération d'une clé SSH** :
1. Ouvrez un terminal ou une invite de commande (sur la VM_MASTER en l'occurence).
2. Tapez la commande suivante pour générer une nouvelle paire de clés SSH (clé privée et clé publique) :
   ```bash
   ssh-keygen -t rsa -b 4096 -C "votre.email@example.com"
   ```

![image](https://github.com/R-D-Y/ansible-awx-course/assets/102509252/49262ba8-4e55-417b-910c-bddb242fd407)


   
3. Suivez les instructions à l'écran pour choisir un emplacement pour les clés et, éventuellement, (un mot de passe pour sécuriser la clé privée).

**Ajout de la clé publique à GitHub** :
1. Ouvre le fichier contenant la clé publique (généralement dans `~/.ssh/id_rsa.pub`) et copie son contenu (tu peux faire un `CAT` dessus).

![image](https://github.com/R-D-Y/ansible-awx-course/assets/102509252/ae10c6b0-c1bf-4544-b475-651daa3bf4d6)

   
3. Connectez-vous à votre compte GitHub et accédez à **Settings** > **SSH and GPG keys**.

![image](https://github.com/R-D-Y/ansible-awx-course/assets/102509252/8ecbd928-a459-47e8-b4a3-e85e36821b86)

   
5. Cliquez sur **New SSH key**, donnez un titre à votre clé (nom du pc par exemple) et collez le contenu de la clé publique dans le champ prévu à cet effet.

![image](https://github.com/R-D-Y/ansible-awx-course/assets/102509252/f950e515-591f-4160-b64a-f66f89b2a314)
![image](https://github.com/R-D-Y/ansible-awx-course/assets/102509252/5c9ae7eb-219d-4896-83a9-43d4892ade04)


6. Cliquez sur **Add SSH key** pour ajouter la clé à votre compte GitHub.

![image](https://github.com/R-D-Y/ansible-awx-course/assets/102509252/0ac0e69d-19ac-4865-bffb-90daa3e0e367)


---

#### **3. Clonage et push avec SSH**

Une fois votre clé SSH ajoutée à GitHub, vous pouvez cloner des dépôts et pousser des modifications en utilisant SSH au lieu de HTTPS, donc beaucoup plus simple. Plus besoin de renseigner de mot de passe, tout passera par SSH, tu pourra télécharger du code, pousser du code, faire des modifications.... En bref, tout ce qui était faisable depuis le GUI pourra être fait depuis ton p'tit terminal !

**Clonage d'un dépôt avec SSH** :
```bash
git clone git@github.com:NomUtilisateur/NomDepot.git
```

![image](https://github.com/R-D-Y/ansible-awx-course/assets/102509252/e14fff04-b15e-4a2b-9c30-8571fd176159)


**Push des modifications avec SSH** :
Après avoir effectué vos commits localement, tu peux pousser tes modifications vers GitHub en utilisant SSH. La commande reste la même (`git push`), mais la connexion est établie via SSH, plus besoin d'interface graphique !

![image](https://github.com/R-D-Y/ansible-awx-course/assets/102509252/f2e2a08d-f1af-4cbb-bb93-7fdafccca188)


---

Processus de génération, d'ajout d'une clé SSH à GitHub, et d'interaction avec GitHub via SSH :

![Processus SSH avec GitHub](https://showme.redstarplugin.com/d/d:gNlHBuVZ)

---

# **[6] Collaboration et Contribution avec GitHub**

---

#### **1. Forking et création de pull requests**

Le processus de "forking" est une méthode très utilisé pour la contribution dans les projets. Il vous permet de créer une copie d'un projet externe sur notre propre compte GitHub, d'y apporter des modifications, puis de proposer ces modifications au dépôt original via une "pull request".

**Étapes pour forker un dépôt et créer une pull request** :
1. **Forker le dépôt** : Cliquez sur le bouton "Fork" en haut à droite de la page du dépôt que vous souhaitez contribuer. Cela créera une copie du dépôt sur votre compte GitHub (je prend par exemple le projet de mon collègue Bochi auquel je souhaite apporter une modification.

![image](https://github.com/R-D-Y/ansible-awx-course/assets/102509252/38246d3b-74b9-4dc6-9734-d5e9ab4d9f75)

![image](https://github.com/R-D-Y/ansible-awx-course/assets/102509252/3057d273-7d83-41fb-bf9c-b7162eab5b01)

![image](https://github.com/R-D-Y/ansible-awx-course/assets/102509252/3b780722-92d2-4fd9-bbea-7b5941b763b5)

et voilà, je me retrouve avec le projet de Bochi, sur mon compte github ! 

![image](https://github.com/R-D-Y/ansible-awx-course/assets/102509252/cbcb3836-e178-4838-98bd-c2cd616e4c1f)


3. **Clonez votre fork** : Clonez le dépôt forké sur votre machine locale pour y apporter des modifications, comme appris précédemment, je vais le cloner pour qu'il se retrouve en local sur mon poste avec la commande `git clone git@github.com:R-D-Y/NomDuProjet.git`.

![image](https://github.com/R-D-Y/ansible-awx-course/assets/102509252/f13be424-7d8c-4e3c-a46c-89ef95f570c1)

   
5. **Apportez vos modifications** : Une fois le projet en local, libre à vous d'apporter les options souhaités!


   
7. **Créez une pull request** : Retournez à la page du dépôt original et cliquez sur "New Pull Request". Sélectionnez votre fork et la branche sur laquelle vous avez travaillé, puis soumettez la pull request !! 

![image](https://github.com/R-D-Y/ansible-awx-course/assets/102509252/509caa61-7e0e-4202-9a46-d283edc94ab7)

8. **Usage perso ??** : Et oui, après votre forks, si la modification que vous avez apporter, est strictement personnel à votre infrastructure, et n'aura aucun plus pour les autres, vous n'êtes évidemment pas obligé de soumettre un pull request, cette dernière sert uniquement à contribué à un projet, afin de pousser vos modifications pour les autres :) .

---

#### **2. Gestion des conflits**

Lorsque plusieurs personnes travaillent sur le même code, évidemment, des conflits peuvent survenir. GitHub fournit donc des outils pour identifier et résoudre ces derniers !

**Résolution des conflits** :
1. Lorsqu'un conflit est détecté, GitHub vous en informera dans la pull request.

![image](https://github.com/R-D-Y/ansible-awx-course/assets/102509252/ad2aae64-29c5-4d61-bd48-196326761871)

2. Ouvrez les fichiers en conflit et recherchez les marqueurs de conflit (`<<<<<<<`, `=======`, `>>>>>>>`).

![image](https://github.com/R-D-Y/ansible-awx-course/assets/102509252/681768d4-1ddc-4e53-80dd-16e91d3320e2)

3. Il suffit de Modifier le code pour résoudre le conflit, puis de supprimer les marqueurs de conflit.
4. Enfin, Committez et poussez les modifications résolues et le tour est joué !

---

#### **3. Code reviews et commentaires**

Les "code reviews" sont essentielles pour maintenir la qualité du code. Lorsqu'une pull request est soumise, Les membres de l'équipe, les contributeurs, ou bien même toutes personnes suivant votre projet de près ou de loin peuvent donner leurs avis (Comme sur les réseaux sociaux!).

**Processus de code review** :
1. Examinez le code soumis dans la pull request.
2. Si vous avez des suggestions ou des corrections, commentez directement sur les lignes de code concernées, dans l'exemple ci-dessous, j'avais fais un petit TP sur Terraform, mon professeur, à la suite de ce TP, a examiner contribuer à mon projet (correctionnel), J'ai donc à mon tour, commenter sa proposition !

![image](https://github.com/R-D-Y/ansible-awx-course/assets/102509252/531ffa98-09b0-40bd-a2f7-957838d046f7)

3. Si tout semble correct, vous pouvez approuver la pull request. Sinon, demandez des modifications avant la fusion. Dans ce même exemple, je ne Mergerais pas la pull request car elle est inutile à mon projet

![image](https://github.com/R-D-Y/ansible-awx-course/assets/102509252/4d27136e-2851-49c6-9be2-79ac59fc2f02)


---

Processus de forking, de création de pull requests, de gestion des conflits et de code reviews sur GitHub :

![Processus de Collaboration et Contribution avec GitHub](https://showme.redstarplugin.com/d/d:fhf19ig3)

*La collaboration et la contribution sont au cœur de la philosophie de GitHub. En suivant ces étapes et en adoptant les bonnes pratiques, vous pouvez contribuer efficacement à des projets et assurer une qualité de code élevée.*

---

# **[7] Fonctionnalités Avancées de GitHub**

---

#### **1. GitHub Actions la CI/CD**

**GitHub Actions** est un outil d'automatisation clé en main qui permet de définir des workflows personnalisés pour créer une pipeline directement depuis votre dépôt GitHub. En d'autre terme, Github action permet de faire de la CI/CD...

 <a href="url"><img src="https://github.com/R-D-Y/ansible-awx-course/assets/102509252/4ed736b4-edb2-4115-b019-37033ae5e75a" height="45%" width="45%" ></a>

- **CI (Intégration Continue)** : C'est le fait d'automatiser le processus de vérification de chaque modification apportée au code source (vous vous souvenez ? les merges ?), en exécutant un ensemble de tests pour s'assurer que le code est correct. Il va permmettre de valider le fait que la modification que vous avez apporté n'impacte pas l'environnement de production !

- **CD (Livraison Continue)** : C'est la prochaine étape après l'Intégration Continue. Elle se concentre sur la livraison automatique de code vérifié à la production. Et oui, une fois les tests effectués, pourquoi attendre ? la partie CD va permettre de pousser vos modification directement en production !

- **Automatisation des workflows** : Avec GitHub Actions, vous pouvez automatiser tous les aspects du développement de votre projet, comme la construction, les tests, le déploiement, etc. Vous pouvez par exemple faire un workflow avec Github action, pourra faires ces actions: dès qu'une modification est apporté au code, il lance des tests automatique, si les tests n'aboutissent pas, il t'envoie un petit mail pour te dire là ou ça coince, sinon, il pousse ton code directement en production ! Dans ce cas précis, il s'agit de CI/CD, l'intégration as été validé, puis le déploiement a été mis en place !

---

#### **2. Utilisation de GitHub Pages pour tes sites web**

**GitHub Pages** est un service d'hébergement gratuit qui prend votre code HTML, CSS et JavaScript, construit à partir d'un dépôt GitHub, et le transforme en un site web... et oui, Github stock du code, mais pas que ! tu peux aussi t'en servir pour héberger ton site web et ce de façon gratuite, parfait pour faire un petit blog!



 <a href="url"><img src="https://github.com/R-D-Y/ansible-awx-course/assets/102509252/54c4e68f-3fc3-45c4-86bc-e37499a7d857" height="30%" width="30%" ></a>





- **Personnalisation des thèmes** : GitHub Pages supporte Jekyll, ce qui signifie que tu peux personnaliser l'apparence de ton site en choisissant parmi les thèmes disponibles ou en créant le vôtre, parfait si tu n'est pas un expert du front-end. (pour information Jekyll est un générateur de site statique! comme Wordpress!).

  ![image](https://github.com/R-D-Y/ansible-awx-course/assets/102509252/9e3b2935-54ed-4797-ad3f-cf4f03c68a25)

- **Domaines personnalisés ? c'est possible!** : Tu peux évidemment ajouter ton propre nom de domaine à ton site *GitHub Pages* pour lui donner une adresse web professionnelle, oublie le github.TonPseudo.io ! tu pourra très facilement mettre ton nom.prenom par exemple...

---

#### **3. GitHub Packages**

**GitHub Packages** C'est un service d'hébergement de packages qui te permet d'héberger tes packages de logiciels et de s'en servir comme des dépendances de ton projet ! (un peu comme un requirement.exe) > [ICI](https://github.com/features/packages)

![image](https://github.com/R-D-Y/ansible-awx-course/assets/102509252/d0148b6c-63de-43da-9083-4aa8ebfe3c58)


- **Partage de packages de code** : Tu peux héberger tes packages et les rendres disponibles dans tous les langages de programmation.

- **Intégration dans github** : Évidemment ce dernier s'intègre avec GitHub, dans tes projets, donc tu peux utiliser le même flux de travail pour le code source et les packages. Tout peut-être stocker au même endroit, et de façon `all-in-one` avoir tout de disponible en 1 `git-clone` !

- **Gestion des versions** : Tu peux publier de nouvelles versions de vos packages et définir des versions spécifiques comme dépendances dans tes projets. Donc de la même manière que tu créer des branches pour versionner ton projet avec du code, ici, avec tes packages, tu peux forcer a utiliser tel ou tel dépendance, dans tel ou tel version selon le client que tu auras en face... Il est sur Windows ? utilise celles-ci, il est sur MacOS ? utilise celles-là :)

---

Les fonctionnalités avancées de GitHub :

![Fonctionnalités Avancées GitHub](https://showme.redstarplugin.com/d/d:HzGXSzbA)


*GitHub va offrire énormément fonctionnalités avancées qui permettent qui permettent de travailler de manière plus efficace, de collaborer avec d'autres et de déployer des projets de manière sécurisée et fiable et surtout, très rapidement. Ces outils, lorsqu'ils sont utilisés correctement et ensemble, peuvent grandement améliorer la productivité des équipes. Il s'agît de la raison principale pour laquelle Github, combinés à ses fonctionnalités, font qu'ils sont leaders sur ce marché.*

---



# **[8] Conclusion sur GitHub**

---

#### **1. Résumé des points clés**

Au cours de cette session, nous avons exploré en profondeur les différentes facettes de GitHub !

- **Introduction à GitHub** : Nous avons découvert ce qu'est GitHub, pourquoi il est essentiel pour travailler en équipe et comment il se distingue de Git.

- **Interface Graphique** : Nous avons navigué à travers l'interface utilisateur de GitHub, afin de comprendre ce qui était possible de faire à partir de l'interface web, et pris connaissance des utilisations de base de ce dernier.

- **Github CLI** : Nous avons abordé les commandes Git essentielles pour la gestion des dépôts (git & push), des commits, des branches, et bien plus encore...

- **Bonnes Pratiques** : Nous avons discuté des méthodes de bonens pratiques pour une bonne utilisation de cet outil, de façon productive et sécurisé.

- **Sécurité & Clés SSH** : Point de vue sur l'importance des clés SSH : pour une connexion sécurisée et surtout plus simple ! 

- **Collaboration et Contribution** : Nous avons appris comment collaborer efficacement avec d'autres, savoir gérer les conflits, et appris la manière dont nous pouvions contribuer à des projets autant en interne, qu'en Open-Source!
  
- **Fonctionnalités Avancées** : Nous avons découvert quelques outils proposés par Github tels que GitHub Actions, GitHub Pages, et GitHub Packages. (Il en existe encore beaucoup croyez-moi!).

---

#### **2. Pour aller plus loin...**

Pour approfondir tes connaissances sur GitHub, voici quelques ressources utiles :

- **Documentation officielle et blog** : La [documentation de GitHub](https://docs.github.com/) est une ressource inestimable pour comprendre toutes les fonctionnalités de la plateforme. Pour des sujets peut-être spécifique, ou des mises en oeuvre concrète, je te conseil le blog de [Stéphane Robert](https://blog.stephane-robert.info/) qui m'a aidé plus d'une fois!
- **Vidéos Youtube** : Beaucoup de vidéastes spécialisés en informatique mettent en oeuvre beaucoup de tuto sur Github, même si ce cours servira amplement, rien ne vous empêche de faire de la veille à ce sujet :).
- **Des soucis ?** : Github, ayant une large communeauté, vous n'aurez aucun mal à trouver de l'aide, sur le [forum interne](https://github.com/topics/forums) ou encore sur [stackoverflow](https://stackoverflow.com/). 
---

#### **3. GitLab**

Alors que nous avons principalement discuté de GitHub dans ce cours, il est également important de mentionner **GitLab**, c'est une autre plateforme populaire de gestion de code source. GitLab offre des fonctionnalités similaires à GitHub mais se distingue par certaines fonctionnalités, Gitlab est un projet Open-Source et donc gratuit, et ce dernier peut-être installer en local. Sur ce même sujet, il nest pas rare en entreprise d'utiliser Gitlab et github, car sans accès web, Gitlab est un bon remède, parfait pour des serveurs qui n'ont pas d'accès web pour des raisons de sécurités, ceux-ci peuvent par exemple aller chercher des sources sur Gitlab! C'est un autre sujet, nous n'en n'aurons pas besoin pour notre projet, mais n'hésitez pas à vous renseigner à ce sujet.

---

#### **4. Exercices pratiques**

Pour consolider tes connaissances, il est essentiel de mettre en pratique ce que nous avons pu t'apprendre. Dans la section suivante, nous allons proposer quelques exercices pratiques pour tester et renforcer tes compétences sur GitHub.

---


Conclusion et les points clés abordés sur GitHub :

![Conclusion GitHub](https://showme.redstarplugin.com/d/d:vq6sffLA)


