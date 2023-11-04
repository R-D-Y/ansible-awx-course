
# **[1] Présentation d'Ansible**

**Qu'est-ce qu'Ansible?**

Ansible est un outil d'automatisation IT open-source qui permet d'automatiser des tâches telles que la configuration de serveurs, le déploiement d'applications et la gestion de l'infrastructure. Contrairement à d'autres outils d'automatisation, Ansible est conçu pour être minimaliste et facile à utiliser. Il utilise un langage de description simple, YAML, pour définir les tâches d'automatisation.

- **Pourquoi utiliser Ansible?**
  - Ansible offre une approche simple et efficace pour automatiser les tâches sans nécessiter de scripts complexes ou de langages de programmation spécialisés.
  
- **Avantages d'Ansible**
  - Facilité d'utilisation : Ansible utilise un langage de description simple (YAML) pour définir les tâches d'automatisation.
  - Agentless : Contrairement à d'autres outils, Ansible n'a pas besoin d'agents installés sur les machines cibles.
  - Extensible : Ansible dispose d'une vaste bibliothèque de modules pour gérer différents systèmes et services.

**Exemple**:
Supposons que vous souhaitiez installer Apache sur un serveur. Avec Ansible, cela pourrait ressembler à ceci en YAML:
```yaml
---
- name: Installer Apache
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
Il s'agit de la machine sur laquelle Ansible est installé et à partir de laquelle les commandes sont exécutées. Le nœud de contrôle se connecte aux nœuds gérés via SSH, sans nécessiter d'agent sur les machines distantes.

**Nœuds gérés**:
Ce sont les machines sur lesquelles les tâches Ansible sont exécutées. Elles sont définies dans l'inventaire Ansible.

**Modules**:
Les modules Ansible sont des unités de code qui exécutent des tâches spécifiques. Par exemple, le module `yum` est utilisé pour gérer les paquets sur les systèmes Red Hat, tandis que le module `apt` est utilisé pour les systèmes Debian.

**Inventaire**:
L'inventaire est un fichier qui contient la liste des nœuds gérés. Il peut être statique (fichier texte) ou dynamique (script ou service externe).

---

### **Inventaire Ansible**

**Hôtes et groupes**:
Dans l'inventaire, vous pouvez définir des hôtes individuels ou les regrouper pour une gestion plus facile.

**Inventaires statiques**:
Il s'agit de fichiers texte simples qui listent les nœuds gérés, généralement en format INI ou YAML.

**Inventaires dynamiques**:
Pour les environnements plus complexes ou changeants, Ansible peut utiliser des scripts ou des services externes pour générer l'inventaire.




![Introduction à Ansible](https://showme.redstarplugin.com/d/d:8azQPrPa)


---

### **[2] Hôtes et groupes**

Dans Ansible, les **hôtes** sont les machines sur lesquelles vous souhaitez exécuter des commandes ou installer quelque chose. Les hôtes sont définis dans l'inventaire Ansible. Pour faciliter la gestion, vous pouvez regrouper plusieurs hôtes en **groupes**. Par exemple, tous vos serveurs web peuvent être regroupés sous le nom "web" et vos bases de données sous le nom "db".

**Exemple**:

Supposons que vous ayez trois serveurs web et deux bases de données. Votre fichier d'inventaire pourrait ressembler à ceci:

```ini
[web]
webserver1.example.com
webserver2.example.com
webserver3.example.com

[db]
dbserver1.example.com
dbserver2.example.com
```

---

### **Inventaires statiques et dynamiques**

**Inventaires statiques**:
Il s'agit de fichiers texte simples qui listent les nœuds gérés, généralement en format INI ou YAML. Ces fichiers sont faciles à écrire et à comprendre, mais peuvent ne pas être idéaux pour des environnements dynamiques où les machines sont fréquemment ajoutées ou supprimées.

**Inventaires dynamiques**:
Pour les environnements plus complexes ou changeants, Ansible peut utiliser des scripts ou des services externes pour générer l'inventaire. Par exemple, si vos serveurs sont dans AWS, un script d'inventaire dynamique peut interroger AWS pour obtenir la liste des instances EC2.

---

# **Commandes Ad-hoc**

Les commandes ad-hoc sont des commandes Ansible que vous pouvez exécuter de manière ponctuelle pour effectuer une tâche simple, sans écrire un playbook. Elles sont utiles pour des tâches rapides, mais pour des tâches plus complexes ou répétitives, il est préférable d'utiliser des playbooks.

**Exemple**:

Pour vérifier l'uptime de tous vos serveurs web, vous pourriez exécuter:

```bash
ansible web -i inventory.ini -m command -a "uptime"
```

Ici, `-i` spécifie l'inventaire, `-m` spécifie le module à utiliser (dans ce cas, "command") et `-a` spécifie les arguments à passer au module.


Il existe d'autres commandes ad-hoc utiles telles que le ping de tous les hôtes, l'obtention d'informations sur l'espace disque, le redémarrage des serveurs, l'installation de paquets et la copie de fichiers vers des hôtes.

1. **Ping tous les hôtes**:
   ```bash
   ansible all -i inventory.ini -m ping
   ```
   Cette commande vérifie la connectivité de tous les hôtes définis dans l'inventaire.

2. **Obtenir des informations sur l'espace disque**:
   ```bash
   ansible web -i inventory.ini -m command -a "df -h"
   ```
   Cette commande affiche l'espace disque sur tous les serveurs web.

3. **Redémarrer tous les serveurs d'une base de données**:
   ```bash
   ansible db -i inventory.ini -m command -a "/sbin/reboot"
   ```

4. **Installer un paquet sur des serveurs Debian/Ubuntu**:
   ```bash
   ansible web -i inventory.ini -m apt -a "name=nginx state=present"
   ```
   Cette commande installe le serveur web nginx sur tous les serveurs web qui utilisent Debian ou Ubuntu.

5. **Copier un fichier vers des hôtes**:
   ```bash
   ansible web -i inventory.ini -m copy -a "src=/local/path/file.txt dest=/remote/path/file.txt"
   ```
   Cette commande copie un fichier local vers un chemin spécifié sur les serveurs web.


---

Commande Ad-hoc à travers Ansible:
![Exécution d'une commande Ad-hoc avec Ansible](https://showme.redstarplugin.com/d/d:DwAuamwV)


---

# **[3] Modules Ansible**

---

#### **Présentation des modules**

**Qu'est-ce qu'un module?**  
Un module Ansible est une unité de code qui exécute une tâche spécifique. Chaque module est conçu pour être idempotent, ce qui signifie qu'il peut être exécuté plusieurs fois sans changer le résultat final, à moins que quelque chose n'ait changé sur le système cible.

**Pourquoi utiliser des modules?**  
Les modules encapsulent des tâches spécifiques, fournissant une interface abstraite pour effectuer des opérations courantes. Cela signifie que vous n'avez pas besoin de connaître les détails spécifiques de la façon dont une opération est effectuée sur chaque système d'exploitation ou plateforme. Par exemple, le module `package` peut être utilisé pour installer un logiciel, que vous soyez sur un système utilisant `apt`, `yum`, ou un autre gestionnaire de paquets.

**Types de modules**  
Il existe des centaines de modules Ansible pour gérer presque tous les aspects de votre environnement, des opérations de base du système d'exploitation, la gestion des services cloud, la gestion des bases de données, et bien plus encore.

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

Un playbook Ansible est un fichier YAML qui définit une série de tâches à exécuter sur des hôtes cibles. Chaque playbook est composé de un ou plusieurs "plays", et chaque "play" définit un ensemble de tâches à exécuter sur un groupe d'hôtes.

La structure typique d'un playbook est la suivante:

```yaml
---
- name: Nom du play
  hosts: groupe_d_hotes
  tasks:
    - name: Nom de la tâche
      module:
        paramètre1: valeur1
        paramètre2: valeur2
```

**Exemple**:

Supposons que vous souhaitiez installer Apache sur un groupe de serveurs web. Votre fichier d'inventaire `inventaire.ini` pourrait ressembler à ceci:

```ini
[web]
webserver1.example.com
webserver2.example.com
webserver3.example.com
```

Et votre playbook `installer_apache.yml` serait:

```yaml
---
- name: Installer Apache sur les serveurs web
  hosts: web
  tasks:
    - name: Installer le paquet httpd
      yum:
        name: httpd
        state: present
```

---

#### **Création et exécution de playbooks**

**Création**:
1. Commencez par créer un fichier avec l'extension `.yml` ou `.yaml` pour le playbook et un fichier `.ini` pour l'inventaire.
2. Utilisez un éditeur de texte ou un IDE pour écrire votre playbook et votre inventaire en suivant les structures mentionnées ci-dessus.
3. Sauvegardez les fichiers.

**Exécution**:
Pour exécuter un playbook en utilisant un inventaire spécifique, utilisez la commande `ansible-playbook` suivie du nom du fichier playbook et de l'option `-i` pour spécifier l'inventaire:

```bash
ansible-playbook -i inventaire.ini installer_apache.yml
```

---

Création et l'exécution d'un playbook Ansible avec un inventaire spécifique:
![Création et exécution d'un playbook Ansible avec inventaire](https://showme.redstarplugin.com/d/d:FJDX23yZ)


---

# **[5] Gestion des Variables**

---

#### **Définition et utilisation des variables**

**Qu'est-ce qu'une variable?**  
Dans Ansible, une variable est une étiquette associée à une valeur, qui peut être utilisée pour personnaliser le comportement des playbooks et des rôles. Les variables permettent de rendre les playbooks réutilisables et de s'adapter à différents environnements ou configurations.

**Comment définir une variable?**  
Les variables peuvent être définies de plusieurs manières:

- Directement dans les playbooks.
- Dans des fichiers d'inventaire.
- Dans des fichiers de variables externes.
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

Dans cet exemple, les variables `http_port` et `max_clients` sont définies et utilisées dans le playbook.

---

#### **Priorité des variables**

La priorité des variables est un concept important dans Ansible, car il détermine quelle valeur sera utilisée si une variable est définie à plusieurs endroits.

**Ordre de priorité**:

1. **Variables passées en ligne de commande** : Elles ont la priorité la plus élevée.
2. **Variables définies dans les rôles** : Ces variables ont une priorité inférieure aux variables passées en ligne de commande, mais supérieure aux variables définies dans les playbooks.
3. **Variables définies dans les playbooks** : Elles ont une priorité inférieure aux variables définies dans les rôles.
4. **Variables d'inventaire** : Elles ont la priorité la plus basse.

---

Gestion des variables dans Ansible:
![Gestion des Variables](https://showme.redstarplugin.com/d/d:XT0RWmcW)



---

# **[6] Gestion des Variables**

---

#### **Définition et utilisation des variables**

**Qu'est-ce qu'une variable?**  
Dans Ansible, une variable permet de stocker une valeur que vous pouvez utiliser plus tard dans votre playbook. Les variables peuvent être définies de plusieurs manières, notamment dans des fichiers d'inventaire, dans des playbooks, dans des fichiers de variables, ou même à partir de la ligne de commande.

**Comment définir une variable?**  
Les variables peuvent être définies directement dans un playbook, dans un fichier d'inventaire, ou dans un fichier de variables séparé. Par exemple, dans un playbook:

```yaml
vars:
  nom_utilisateur: admin
```

Ou dans un fichier d'inventaire:

```ini
[web]
webserver1.example.com http_port=80
```

**Utilisation des variables dans les playbooks**  
Une fois qu'une variable est définie, elle peut être utilisée dans un playbook en l'entourant de doubles accolades `{{ }}`. Par exemple:

```yaml
- name: Créer un utilisateur
  user:
    name: "{{ nom_utilisateur }}"
    state: present
```

---

#### **Priorité des variables**

La priorité des variables détermine quelle valeur sera utilisée si une variable est définie à plusieurs endroits. Voici l'ordre de priorité, du plus bas au plus élevé:

1. **Variables d'inventaire**: Définies dans le fichier d'inventaire.
2. **Variables de rôle**: Définies dans le dossier `defaults` d'un rôle.
3. **Variables définies dans les playbooks**: Définies directement dans un playbook.
4. **Variables passées en ligne de commande**: Définies lors de l'exécution d'un playbook à l'aide de l'option `-e`.

---

Gestion des variables dans Ansible:
![Gestion des Variables](https://showme.redstarplugin.com/d/d:lOqeKh7T)



---

# **[7] Vault Ansible**

---

#### **Sécurisation des données sensibles avec Ansible Vault**

Dans le monde de l'automatisation et de la gestion de configuration, la sécurité des données est primordiale. Ansible, conscient de cette nécessité, a introduit **Ansible Vault**. C'est un mécanisme de chiffrement qui permet de sécuriser n'importe quelle information structurée, garantissant ainsi que les données sensibles restent confidentielles même lorsqu'elles sont stockées dans un système de contrôle de version comme Git.

**Pourquoi utiliser Ansible Vault?**  
- **Confidentialité**: Ansible Vault chiffre les données à l'aide de l'algorithme AES256, garantissant que seules les personnes disposant de la clé de déchiffrement appropriée peuvent accéder aux données.
- **Intégration transparente**: Même si les données sont chiffrées, Ansible peut les utiliser comme n'importe quel autre fichier lors de l'exécution d'un playbook, à condition que le mot de passe correct soit fourni.
- **Flexibilité**: Vous pouvez chiffrer un fichier entier, ou simplement certaines valeurs à l'intérieur d'un fichier.

---

#### **Utilisation d'Ansible Vault**

**Chiffrement d'un fichier**  
Pour chiffrer un fichier entier, utilisez la commande suivante:

```bash
ansible-vault encrypt mon_fichier_secret.yml
```

Lors de l'exécution de cette commande, Ansible Vault vous demandera de fournir un mot de passe. Ce mot de passe sera nécessaire pour toutes les opérations futures sur ce fichier.

**Chiffrement de valeurs spécifiques**  
Si vous ne souhaitez chiffrer que certaines valeurs à l'intérieur d'un fichier, vous pouvez le faire avec la commande `encrypt_string`:

```bash
ansible-vault encrypt_string 'ma_valeur_secrete' --name 'nom_de_la_variable'
```

**Déchiffrement d'un fichier**  
Si vous avez besoin d'accéder au contenu d'un fichier chiffré, vous pouvez le déchiffrer temporairement:

```bash
ansible-vault decrypt mon_fichier_secret.yml
```

**Exécution d'un playbook contenant des données chiffrées**  
Lors de l'exécution d'un playbook qui utilise des données chiffrées, vous devez fournir le mot de passe Vault. Il existe plusieurs méthodes pour le faire, mais la plus courante est d'utiliser l'option `--ask-vault-pass`:

```bash
ansible-playbook mon_playbook.yml --ask-vault-pass
```

---

Processus de chiffrement, de déchiffrement et d'utilisation des données avec Ansible Vault:
![Processus Ansible Vault](https://showme.redstarplugin.com/d/d:ujPO9chU)


---

# **[8] Rôles Ansible**

---

#### **Structure d'un rôle**

Un rôle Ansible est une structure pré-définie permettant d'organiser les tâches et autres données de manière logique. Il est conçu pour être entièrement autonome, ou, avec d'autres rôles, formant une unité de déploiement complète. Les rôles réduisent la duplication et facilitent la réutilisation, ce qui permet de diviser la configuration complexe en composants réutilisables.

**Qu'est-ce qu'un rôle?**  
Un rôle est une façon d'automatiser, de configurer et d'organiser un système. Il est composé de plusieurs composants, tels que les tâches, les gestionnaires, les fichiers, les modèles, etc., qui définissent le comportement et les états souhaités pour une machine ou un groupe de machines.

**Comment créer un rôle?**  
Pour créer un rôle, utilisez la commande `ansible-galaxy`:

```bash
ansible-galaxy init nom_du_role
```

Cette commande crée une structure de dossiers pour le rôle avec des dossiers et des fichiers prédéfinis.

---

#### **Explication des dossiers**

- **tasks**: Contient la liste principale des tâches à exécuter par le rôle.
  - **Définition**: Les tâches sont les actions que Ansible exécutera pour atteindre un état désiré.
  - **Exemple**: Installer un paquet, démarrer un service, etc.

- **handlers**: Contient des gestionnaires, qui sont des tâches déclenchées par d'autres tâches.
  - **Définition**: Les gestionnaires sont similaires aux tâches, mais ne s'exécutent que si une tâche les notifie.
  - **Exemple**: Redémarrer un service si un fichier de configuration a été modifié.

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

# **[9] Bonnes Pratiques Ansible**

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


# **[10] Conclusion**

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


