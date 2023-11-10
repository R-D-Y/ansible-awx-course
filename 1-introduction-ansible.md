  

# **[1] Présentation d'Ansible**

**Qu'est-ce qu'Ansible?**

Ansible, c'est un outil d'automatisation IT open-source très repandue qui permet d'automatiser des tâches par exemple de la configuration de serveurs, du déploiement d'applications et de la gestion de l'infrastructure. Contrairement à d'autres outils d'automatisation, Ansible est conçu pour être minimaliste et facile à utiliser (via une logique assez simpliste de description du besoin). Il utilise un langage de description simple à lire pour l'humain,le YAML, qui permet de définir les tâches d'automatisation.

- **Pourquoi utiliser Ansible?**
  - Ansible offre une approche simple et efficace pour automatiser les tâches sans nécessiter de scripts complexes ou de langages de programmation spécialisés, eh oui ! seul une "description" en YAML suffit a lefaire fonctionner .
  
- **Avantages d'Ansible**
  - Facilité d'utilisation : Ansible utilise YAML pour définir les tâches d'automatisation.
  - Agentless : Contrairement à d'autres outils, Ansible n'a pas besoin d'agents installés sur les machines cibles, il agit depuis un serveur master qui effectue des tâches sur sa cible (il a seulement besoin d'une clé ssh, et de python).
  - Extensible : Ansible dispose d'une vaste bibliothèque de modules pour gérer différents systèmes et services, et comme sur Docker-Hub, Ansible-Galaxy propose des rôles clé en mains créer par la communeauté.

**Exemple**:
Imaginons que tu souhaite installer HTTPD sur un serveur. Avec Ansible, ça pourrait ressembler à ceci en YAML:
```yaml
---
- name: Installer HTTPD
  hosts: serveurs_web
  tasks:
    - name: Installer le paquet httpd
      yum:
        name: httpd
        state: present
```

---

### **Architecture et composants**

**Nœuds de contrôle**:
Il s'agit de la machine sur laquelle Ansible est installé et à partir de laquelle les commandes sont exécutées, nous pouvons aussi l'appeler le Master. Le nœud de contrôle se connecte aux nœuds gérés via SSH, sans nécessiter d'agent sur les machines distantes, les cibles ont parfois besoin de python quand il est nécesssaire de faire tes tâches complexes.

**Nœuds gérés**:
Ce sont les machines sur lesquelles les tâches Ansible sont exécutées. Elles sont définies dans l'inventaire Ansible (fichier inventaire.ini par exemple).

**Modules**:
Les modules Ansible sont des unités de code qui exécutent des tâches spécifiques. Par exemple, le module `yum` est utilisé pour gérer les paquets sur les systèmes Red Hat, tandis que le module `apt` est utilisé pour les systèmes Debian (ils sont directement a écrire dans vos playbook, selon la distribution de votre cible).

**Inventaire**:
L'inventaire est un fichier qui contient la liste des nœuds gérés . Il peut être statique (fichier texte) ou dynamique (script ou service externe par exemple).

---

### **Inventaire Ansible**

**Hôtes et groupes**:
Dans l'inventaire, vous pouvez définir des hôtes individuels ou les regrouper pour une gestion plus facile.

**Inventaires statiques**:
Fichiers texte simples qui listent les nœuds gérés, généralement en format INI ou YAML.

**Inventaires dynamiques**:
Pour les environnements plus complexes ou changeants avec des varaibles, Ansible peut utiliser des scripts ou des services externes pour générer les inventaires.




![Introduction à Ansible](https://showme.redstarplugin.com/d/d:8azQPrPa)


---

### **[2] Hôtes et groupes**

Sur Ansible, les **hôtes**  ou *cibles* sont les machines sur lesquelles vous souhaitez exécuter des commandes ou installer des packets, applications ou autre. Les hôtes sont définis dans l'inventaire Ansible. Pour faciliter la gestion, vous pouvez regrouper plusieurs hôtes en **groupes**. Par exemple, tous vos serveurs web peuvent être regroupés sous le nom "web" et vos bases de données sous le nom "db", et ce à l'infini selon vos projet .

**Exemple**:

Supposons que vous ayez trois serveurs web et deux bases de données: 

```ini
[web]
webserver_a.example.com
webserver_b.example.com
webserver_c.example.com

[db]
dbserver1.example.com
dbserver2.example.com

#vous pouvez y mettre l'adresse IP cible mais cela n'est pas une bonne pratique, le DNS doit toujours être prioritaire !!
```

---

### **Inventaires statiques et dynamiques**

**Inventaires statiques**:
Fichiers texte simples qui listent les nœuds gérés, généralement en format INI ou  au format YAML. Ces fichiers sont faciles à écrire et à comprendre, mais peuvent ne pas être idéaux pour des environnements dynamiques où les machines sont fréquemment ajoutées ou supprimées, pour cela, nous utilisons des Inventaires dynamiques.

**Inventaires dynamiques**:
Pour les environnements plus complexes ou changeants, Ansible peut utiliser des scripts ou des services externes pour générer l'inventaire. Par exemple, si vos serveurs sont dans AWS, un script d'inventaire dynamique peut interroger AWS pour obtenir la liste des instances EC2, puis remplir notre fichier d'inventaire à l'aide de l'output du script.

---

# **Commandes Ad-hoc**

Les commandes ad-hoc... Ce sont les commandes Ansible que vous pouvez exécuter de manière ponctuelle pour effectuer une tâche simple comme faire un ping, sans écrire un playbook. Elles sont utiles pour des tâches rapides, mais pour des tâches plus complexes ou répétitives, il est préférable d'utiliser des playbooks, ou bien même un rôle !

**Exemple**:

Pour vérifier l'uptime de tous vos serveurs web, pas besoin de playbook, faites une commande ah-hoc:

```bash
ansible web -i inventory.ini -m command -a "uptime"
```

Ici, `-i` spécifie l'inventaire, `-m` spécifie le module à utiliser (dans ce cas, "command") et `-a` spécifie les arguments à passer au module.


Il existe d'autres commandes ad-hoc utiles comme le ping de tous les hôtes, l'obtention d'informations sur l'espace disque, le redémarrage des serveurs, l'installation de paquets et la copie de fichiers vers des hôtes.

1. **Ping tous les hôtes**:
   ```bash
   ansible all -i inventory.ini -m ping
   ```
   La commande vérifie la connectivité de tous les hôtes définis dans l'inventaire.

2. **Obtenir des informations sur l'espace disque**:
   ```bash
   ansible web -i inventory.ini -m command -a "df -h"
   ```
   La commande affiche l'espace disque sur tous les serveurs web.

3. **Redémarrer tous les serveurs d'une base de données**:
   ```bash
   ansible db -i inventory.ini -m command -a "/sbin/reboot"
   ```

4. **Installer un paquet sur des serveurs Debian/Ubuntu**:
   ```bash
   ansible web -i inventory.ini -m apt -a "name=nginx state=present"
   ```
   La commande installe le serveur web nginx sur tous les serveurs web qui utilisent Debian ou Ubuntu.

5. **Copier un fichier vers des hôtes**:
   ```bash
   ansible web -i inventory.ini -m copy -a "src=/local/path/file.txt dest=/remote/path/file.txt"
   ```
   La commande copie un fichier local vers un chemin spécifié sur les serveurs web.


---

Commande Ad-hoc à travers Ansible:
![Exécution d'une commande Ad-hoc avec Ansible](https://showme.redstarplugin.com/d/d:DwAuamwV)


---

# **[3] Modules Ansible**

---

#### **Présentation des modules**

**Qu'est-ce qu'un module?**  
Un module Ansible est une unité de code qui exécute une tâche spécifique donné. Chaque module est conçu pour être idempotent, donc il peut être exécuté plusieurs fois sans changer le résultat final, à moins que quelque chose n'ait changé sur le système cible (OK/CHANGED/ERROR).

**Pourquoi utiliser des modules?**  
Les modules encapsulent des tâches spécifiques, en fournissant une interface pour effectuer des opérations courantes.De ce fait, vous n'avez pas besoin de connaître les détails spécifiques de la façon dont une opération est effectuée sur chaque OS ou plateforme. Par exemple, le module `package` peut être utilisé pour installer un logiciel, que vous soyez sur un système utilisant `apt`, `yum`, ou un autre gestionnaire de paquets, cela arrivera à la même finalité, Ansible, étant intelligent va pouvoir savoir quelle commande utiliser en back-end.

**Types de modules**  
Il existe des centaines de modules Ansible pour gérer presque tous les aspects de votre environnement, des opérations de base du système d'exploitation, la gestion des services cloud, la gestion des bases de données, et bien plus encore. Comme expliqué précédemment, sur Ansible-Galaxy, vous pouvez trouver playbook, rôle et autre créer par la communeauté, et évidemment, certains modules créer par la communeauté peuvent vous servir !!

---

#### **Utilisation des modules populaires**

**module `apt`**  
Utilisé pour gérer les paquets sur les systèmes Debian/Ubuntu.  
*Exemple* : Pour installer le paquet `nginx` :  
```yaml
- name: Installer nginx
  apt:
    name: nginx
    state: present
```

**module `yum`**  
Utilisé pour gérer les paquets sur les systèmes Red Hat/CentOS.  
*Exemple* : Pour installer le paquet `httpd` :  
```yaml
- name: Installer httpd
  yum:
    name: httpd
    state: present
```

**module `copy`**  
Copie des fichiers depuis le nœud de contrôle vers les nœuds gérés.  
*Exemple* : Pour copier un fichier `index.html` vers un serveur web :  
```yaml
- name: Copier index.html
  copy:
    src: /local/path/index.html
    dest: /var/www/html/index.html
```

**module `file`**  
Gère les fichiers et les propriétés des fichiers.  
*Exemple* : Pour s'assurer qu'un répertoire `/data` existe :  
```yaml
- name: Assurer que le répertoire /data existe
  file:
    path: /data
    state: directory
```

**module `service`**  
Gère les services sur les systèmes d'exploitation qui utilisent des systèmes d'init comme systemd, upstart, etc.  
*Exemple* : Pour s'assurer que le service `nginx` est démarré :  
```yaml
- name: Démarrer le service nginx
  service:
    name: nginx
    state: started
```

---

Modules Ansible et leur utilisation:
![Modules Ansible](https://showme.redstarplugin.com/d/d:Ht6ADzRE)


---

# **[4]Les Playbooks**

---

#### **Structure d'un playbook**

Le playbook Ansible est un fichier en YAML qui va définir une série de tâches à exécuter sur nos cibles. Chaque playbook est composé de un ou plusieurs "play". Chaque "play" définit un ensemble de tâches qui vont être à exécuter sur mon ou mes hôtes.

La structure typique d'un playbook est la suivante:

```yaml
---
- name: Nom du play
  hosts: groupe_d_hotes
  tasks:
    - name: Nom de la tâche 1 #comme exepliquer il peut y en avoir plusieurs selon le besoin
      module:
        paramètre1: valeur1
        paramètre2: valeur2
```

**Exemple**:

Supposons que vous souhaitiez installer NIGNX sur un groupe de serveurs web. Votre fichier d'inventaire `inventaire.ini` pourrait ressembler à ceci:

```ini
[web]
webserver1.example.com
webserver2.example.com
webserver3.example.com
```

Et votre playbook `installer_NGINX.yml` serait:

```yaml
---
- name: Installer HTTPD sur les serveurs web
  hosts: web
  tasks:
    - name: Installer le paquet httpd
      yum:
        name: httpd
        state: present
```

>Nous définissons nos cible sous le groupe "web", puis dans notre playbook, nous indiquons que nos hosts seront le groupe cible.
---

#### **Création et exécution de playbooks**

**Création**:  **Il s'agit là d'un exemple de création, il n'est pas a réaliser maintenant, des exercices viendront en fin de chapitre.**
1. Commencez par créer un fichier `.yml` ou `.yaml` pour le playbook puis un fichier `.ini` pour l'inventaire.
2. Utilisez un éditeur decode/texte de votre choix pour écrire votre playbook et votre inventaire en suivant les structures mentionnées ci-dessus.
3. Sauvegardez les fichiers.

**Exécution**:
Pour exécuter un playbook en utilisant un inventaire spécifique, utilisez la commande `ansible-playbook` suivie du nom du fichier playbook et de l'option `-i` pour spécifier l'inventaire:

```bash
ansible-playbook -i inventaire.ini installer_NGINX.yml
```

---

Création et l'exécution d'un playbook Ansible avec un inventaire spécifique:
![Création et exécution d'un playbook Ansible avec inventaire](https://showme.redstarplugin.com/d/d:FJDX23yZ)


---

# **[5] Gestion des Variables**

---

#### **Définition et utilisation des variables**

**Qu'est-ce qu'une variable?**  
Dans Ansible, une variable est une étiquette associée à une valeur, qui va généralement être utilisée pour personnaliser le comportement des playbooks et des rôles (extrmement fréquent en industrialisation). Les variables permettent de rendre les playbooks réutilisables et de s'adapter à différents environnements ou configurations. > cela permet entre-autre de ne pas avoir a modifier les playbook à la source, une bonne pratique est de créer un fichier de variables spécifique.

**Comment définir une variable?**  
Les variables peuvent être définies de plusieurs manières:

- Directement dans les playbooks (clé-valeur).
- Dans des fichiers d'inventaire.
- Dans des fichiers de variables externes (meilleur pratique pour de l'industrialisation).
- Passées en ligne de commande lors de l'exécution d'un playbook.

**Exemple**:

```yaml
---
- hosts: web
  vars:
    http_port: 80
    max_clients: 200
  tasks:
    - name: assurez-vous que le port HTTP est configuré
      template:
        src: templates/httpd.conf.j2
        dest: /etc/httpd/conf/httpd.conf
```

Dans l'exemple, les variables `http_port` et `max_clients` sont définies et utilisées dans le playbook directement.

```yaml
vars:
  nom_utilisateur: admin
```

Ou dans un fichier d'inventaire:

```ini
[web]
webserver1.example.com http_port=80
```

Une fois qu'une variable est définie, elle peut être utilisée dans un playbook en l'entourant de doubles accolades `{{ }}`. Par exemple:

```yaml
- name: Créer un utilisateur
  user:
    name: "{{ nom_utilisateur }}"
    state: present
```



#### **Priorité des variables**

La priorité des variables est important dans Ansible, car ça détermine quelle valeur sera utilisée si une variable est définie à plusieurs endroits.

**Ordre de priorité**:

1. **Variables passées en ligne de commande** : Elles ont la priorité la plus élevée.
2. **Variables définies dans les rôles** : Ces variables ont une priorité inférieure aux variables passées en ligne de commande, mais supérieure aux variables définies dans les playbooks.
3. **Variables définies dans les playbooks** : Elles ont une priorité inférieure aux variables définies dans les rôles.
4. **Variables d'inventaire** : Elles ont la priorité la plus basse.


![image](https://github.com/R-D-Y/ansible-awx-course/assets/102509252/941a25ed-0d6c-4ddb-bda9-59cb0e6b209b)

---




# **[6] Vault Ansible**

---

#### **Sécurisation des données sensibles avec Ansible Vault**

Dans l'automatisation et la gestion de configuration en IT, la sécurité des données est primordiale. Ansible, conscient de cette nécessité, a introduit **Ansible Vault**: un mécanisme de chiffrement qui permet de sécuriser n'importe quelle information structurée, qui garantirra ainsi que les données sensibles restent confidentielles même lorsqu'elles sont stockées dans un système de contrôle de version comme Git.
(c'est équivalent au Vault de HashiCorp pour les connaisseurs !!).

**Pourquoi utiliser Ansible Vault?**  
- **Confidentialité**: Ansible Vault chiffre les données à l'aide de l'algorithme AES256, seules les personnes disposant de la clé de déchiffrement peuvent accéder aux données stockés.
- **Intégration transparente**: Même si les données sont chiffrées, Ansible peut les utiliser comme n'importe quel autre fichier lors de l'exécution d'un playbook ou d'un rôle, à condition que le bon password soit donné
- **Flexibilité**: Vous pouvez chiffrer un fichier entier, ou simplement certaines valeurs à l'intérieur d'un fichier. (ligne ou structure entière).

---

#### **Utilisation d'Ansible Vault**

**Chiffrement d'un fichier**  
Pour chiffrer un fichier entier, utilisez la commande:

```bash
ansible-vault encrypt mon_fichier_secret.yml
```

Lors de l'exécution de cette commande, Ansible Vault vous demandera de fournir un mot de passe. Ce mot de passe sera nécessaire pour toutes les opérations futures sur ce fichier donc retenez le bien !!!

**Chiffrement de valeurs spécifiques**  
Si vous ne souhaitez chiffrer que certaines valeurs à l'intérieur d'un fichier, vous pouvez le faire avec la commande `encrypt_string`:

```bash
ansible-vault encrypt_string 'ma_valeur_secrete' --name 'nom_de_la_variable'  #va chiffrer seulement la chaîne de caractère souhaitée)
```

**Déchiffrement d'un fichier**  
Si vous avez besoin d'accéder au contenu d'un fichier chiffré, vous pouvez le déchiffrer temporairement:

```bash
ansible-vault decrypt mon_fichier_secret.yml
```

**Exécution d'un playbook contenant des données chiffrées**  
Pendant l'exécution d'un playbook qui utilise du Vault, vous devez fournir le mot de passe précédent. Il existe plusieurs méthodes pour le faire, mais la plus courante est d'utiliser l'option `--ask-vault-pass`:

```bash
ansible-playbook mon_playbook.yml --ask-vault-pass
```
*D'après la documentation officielle*
---

Processus de chiffrement, de déchiffrement et d'utilisation des données avec Ansible Vault:
![Processus Ansible Vault](https://showme.redstarplugin.com/d/d:ujPO9chU)


---

# **[7] Rôles Ansible**

---

#### **Structure d'un rôle**

Un rôle Ansible est une structure pré-définie permettant d'organiser les tâches et autres données de manière logique. Il est conçu pour être entièrement autonome, ou, avec d'autres rôles, formant une unité de déploiement complète. Les rôles réduisent la duplication et facilitent la réutilisation, ce qui permet de diviser la configuration complexe en composants réutilisables, sur Ansible, il s'agit d'un point très important, les rôles c'est la vie !

**Qu'est-ce qu'un rôle concrètement?**  
Un rôle est une façon d'automatiser, de configurer et d'organiser un système. Il est divisé en plusieurs composants : les tâches, les gestionnaires, les fichiers, les modèles, etc., qui définissent le comportement et les états souhaités pour une cible ou un groupe de machines.

**Comment créer un rôle?**  
Pour créer un rôle, utilisez la commande `ansible-galaxy`:

```bash
ansible-galaxy init nom_du_role
```

Cette commande crée une structure de dossiers pour le rôle avec des dossiers et des fichiers prédéfinis, il vous suffit de faire un `tree .` pour la visualiser.

---

#### **Explication des dossiers**

- **tasks**: Contient la liste principale des tâches à exécuter par le rôle.
  - **Définition**: Les tâches sont les actions que Ansible exécutera pour atteindre un état définit.
  - **Exemple**: Installer un paquet, démarrer un service, etc.

- **handlers**: Contient des gestionnaires, qui sont des tâches déclenchées par d'autres tâches.
  - **Définition**: Les gestionnaires sont similaires aux tâches, mais ne s'exécutent que si une tâche les notifie. (multitasking)
  - **Exemple**: Redémarrer un service si un fichier de configuration a été modifié. (if/then)

- **files**: Contient des fichiers qui doivent être déployés par le rôle.
  - **Définition**: Ces fichiers sont copiés tels quels, sans modification.
  - **Exemple**: Fichiers binaires, images, etc.

- **templates**: Contient des modèles qui peuvent être déployés par le rôle.
  - **Définition**: Les modèles sont des fichiers qui peuvent être modifiés par Ansible avant d'être déployés.
  - **Exemple**: Fichiers de configuration avec des variables.

- **vars**: Contient des variables définies pour le rôle.
  - **Définition**: Ces variables sont utilisées pour personnaliser le comportement du rôle.
  - **Exemple**: Version d'un paquet à installer.

- **defaults**: Contient les valeurs par défaut des variables pour le rôle.
  - **Définition**: Ces valeurs sont utilisées si l'utilisateur ne fournit pas de valeur.
  - **Exemple**: Port par défaut pour un service.

- **meta**: Contient des métadonnées sur le rôle, comme les dépendances.
  - **Définition**: Informations sur le rôle, comme l'auteur, la licence, etc.
  - **Exemple**: Autres rôles requis pour que ce rôle fonctionne correctement.


voici un exemple au format tree, puis en diagramme:

![image](https://github.com/R-D-Y/ansible-awx-course/assets/102509252/97a3a921-3a19-42ce-81c0-d34eec7f0841)

---
![Structure d'un Rôle Ansible](https://showme.redstarplugin.com/d/d:JdyrFSvb)

---

# **[8] Bonnes Pratiques Ansible**

---

#### **Organisation du code Ansible**

L'organisation du code est essentielle pour garantir la lisibilité, la maintenabilité et la réutilisabilité du code Ansible. Voici quelques principes clés à suivre:

- **Modularité**:
  - **Utilisation des rôles**: Les rôles permettent de regrouper des tâches, des variables, des fichiers et d'autres éléments en une unité logique. Cela facilite la réutilisation du code et garantit que chaque rôle a une responsabilité unique.
  - **Réutilisation du code**: Évitez de dupliquer le code. Si une tâche ou une fonction est utilisée à plusieurs endroits, envisagez de la transformer en rôle ou en tâche incluse.

- **Clarté**:
  - **Commentaires explicatifs**: Utilisez des commentaires pour expliquer le but de certaines tâches ou décisions. Cela aide les autres développeurs à comprendre votre code.
  - **Éviter la complexité inutile**: Si une tâche peut être accomplie de plusieurs manières, choisissez la plus simple et la plus directe.

---

#### **Conventions de nommage**

Les conventions de nommage aident à garantir que le code est compréhensible et cohérent.

- **Variables**:
  - **Utiliser des noms descriptifs**: Les noms de variables doivent indiquer clairement leur utilisation ou leur valeur.
  - **Éviter les abréviations**: Sauf si elles sont largement reconnues, évitez les abréviations pour garantir la clarté.

- **Fichiers et dossiers**:
  - **Nommage cohérent**: Assurez-vous que les fichiers et les dossiers suivent une convention de nommage cohérente.
  - **Utiliser des tirets pour séparer les mots**: Par exemple, `user-management.yml` plutôt que `usermanagement.yml`.

---

#### **Style**

Le style de codage est tout aussi important que l'organisation et les conventions de nommage.

- **Indentation**:
  - **Utiliser des espaces plutôt que des tabulations**: Cela garantit que le code est affiché de manière cohérente sur différentes plateformes et éditeurs.

- **Consistance**:
  - **Garder un style cohérent à travers le projet**: Cela facilite la lecture et la compréhension du code.

---

Bonnes pratiques Ansible:

![Bonnes Pratiques Ansible](https://showme.redstarplugin.com/d/d:JtpmjyMF)

---


# **[9] Conclusion**

---

#### **Résumé des points clés**

Au cours de cette session, nous avons couvert plusieurs aspects essentiels d'Ansible, notamment:

- **Introduction à Ansible**: Une vue d'ensemble d'Ansible et de ses capacités.
- **Architecture et composants**: Comprendre les éléments fondamentaux qui composent Ansible.
- **Inventaire**: La manière dont Ansible gère et organise les hôtes.
- **Commandes Ad-hoc**: L'exécution de commandes simples sans avoir à écrire un playbook.
- **Modules**: Les blocs de construction utilisés pour effectuer des tâches dans Ansible.
- **Playbooks**: Comment automatiser des tâches avec Ansible en utilisant des playbooks.
- **Gestion des Variables**: Comment définir, utiliser et prioriser les variables.
- **Vault Ansible**: La manière de sécuriser les données sensibles avec Ansible Vault.
- **Rôles Ansible**: Comment organiser vos playbooks et réutiliser le code.
- **Bonnes Pratiques**: Les meilleures pratiques pour écrire et organiser le code Ansible.

---

#### **Ressources pour aller plus loin**

Pour approfondir vos connaissances sur Ansible, voici quelques ressources recommandées:

- **Documentation officielle Ansible**: La source la plus complète et à jour sur Ansible.
- **Forums et communautés Ansible**: Des lieux pour poser des questions, partager des connaissances et apprendre des autres.
- **Livres et tutoriels**: Il existe de nombreux livres et tutoriels qui couvrent Ansible en profondeur.
- **Cours en ligne**: Nous vous proposerons quelques petits exercices afin de mettre en application vos connaissances.

---



![Conclusion et Points Clés](https://showme.redstarplugin.com/d/d:aEmJ9cwL)



