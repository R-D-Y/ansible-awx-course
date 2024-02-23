Comme promis ! vous trouverez ici les corrections des 3 exercices Ansible.

### Correction Exercice 1 - Utilisation des commandes ad-hoc

#### Tâche 1: Utiliser le module `ping`

- **Objectif :** Vérifier la connectivité avec tous les hôtes définis dans votre inventaire.
- **Commande :** 
  ```bash
  ansible all -m ping
  ```
- **Explication :** 

  - `all` spécifie que la commande doit être exécutée sur tout les hôtes, en l'occurrence, notre unique machine vm_node .

  - `-m ping` permet d'utiliser le module `ping`. Il va donc pinguer notre autre, et renvoyer `pong` si les paquets sont passés !

---

#### Tâche 2:  Module `file` pour créer un dossier

- **Objectif :** Créer un dossier `test_directory` dans le répertoire `/tmp` sur notre hôte.
- **Commande :**
  ```bash
  ansible all -m file -a "path=/tmp/test_directory state=directory"
  ```
- **Explication :**
  - `-m file` indique d'utiliser le module `file`.

  - `-a "path=/tmp/test_directory state=directory"` sert pour les arguments à passer au module. Ici, `path` pour le chemin à créer, et `state=directory` indique le type de création, en l'occurrence un dossier. 

--- 

#### Tâche 3: Module `command` pour vérifier l'espace disque

- **Objectif :** Vérifier l'espace disque disponible sur notre hôte
- **Commande :**
  ```bash
  ansible all -m command -a "df -h"
  ```
- **Explication :**
  - `-m command` utilise le module `command`.
  - `-a "df -h"` envoie la commande `df -h` à notre hôte et affiche l'espace disque disponible.

---
---


### Correction Exercice 2 - Création d'un Playbook Simple

#### Objectif :
Créer un playbook `update_system.yml` pour mettre à jour et installer certains paquets sur notre hôte

#### Playbook : `update_system.yml`

```yaml
---
- name: MAJ Update OS
  hosts: vm_node   #(ou mettre son titre de groupe présent dans le fichier inventaire.ini)
  become: yes
  tasks:
    - name: MAJ paquet-list
      apt:
        update_cache: yes

    - name: MAJ Upgrade paquet
      apt:
        upgrade: dist

    - name: Installation de Python
      apt:
        name: python
        state: present

    - name: Installation de NGINX
      apt:
        name: nginx
        state: present
```

et oui... c'est aussi simple que ça, maintenant imaginez de faire sur 50 machines... Un gain de productivité considérable.

#### Explications :

   `become: yes` permet d'exécuter des tâches avec des privilèges root (équivalent du sudo).

- **Tâche 1 - Maj liste des paquets** :

  - Utilisation du module `apt` (utiliser DNF pour du redhat).

  - `update_cache: yes` commande à apt de rafraîchir sa liste de paquets présent.


- **Tâche 2 - Maj des paquets** :

  - Toujours avec le module `apt`.

  - `upgrade: dist` commande à apt pour maj les paquets vers les dernières versions disponibles.


- **Tâche 3 - Installation de Python** :

  - Utilise encore le module `apt`.

  - `name: python` spécifie le paquet à installer (ici, Python).

  - `state: present` assure que le paquet est installé. Si déjà installé, aucune action n'est prise, il skippera sans erreurs.


- **Tâche 4 - Installation de NGINX** :

  - Similaire à la tâche d'installation de Python, mais pour NGINX.

#### Exécution du Playbook :

```bash
ansible-playbook -i inventaire.ini update_system.yml
```

- **`-i inventaire.ini`** pour le fichier d'inventaire où est contenu notre vm_node

- **`update_system.yml`** fichier de playbook que vous exécutez.

---
---

### Correction - Exercice 3 - Création d'un Rôle Simple

#### Objectif :
Créer un rôle `basic_setup` qui effectue des tâches de configuration initiale sur le vm_node.

#### Création du Rôle :

1. **Initialisation du Rôle :**
   Utilisez la commande `ansible-galaxy` pour initialiser la structure du rôle (création du tree) :
   ```bash
   ansible-galaxy init basic_setup
   ```
   Cela va créer un nouveau répertoire `basic_setup` avec la structure de dossiers pour les rôles.

2. **Structure du Rôle :**
   - `tasks`: Tâches principales.
   - `files`: Fichiers à copier sur vm_node.
   - `templates`: Modèles Jinja2.
   - `vars`: Variables du rôle.
   - `defaults`: Valeurs par défaut des variables.
   - `meta`: Informations sur le rôle.

#### Contenu du Rôle :

- **`tasks/main.yml`**:

  ```yaml
  - name: Installer vim
    apt:
      name: vim
      state: present

  - name: Créer un fichier de configuration
    copy:
      src: settings.conf
      dest: /etc/myapp/settings.conf
  ```

- **`files/settings.conf`**:
  Créez un fichier de configuration simple:

  ```
  # settings.conf
  antoine=sanofi
  remi=grandlyon
  ```

#### Explications :

- **Tâche 1 - Installer vim** :
  - Utilise le module `apt` pour installer vim.
  - `state: present` s'assure que vim est bien installé.

- **Tâche 2 - Créer un fichier de configuration** :
  - Utilise le module `copy` pour copier le fichier `settings.conf` depuis le dossier `files` du rôle vers le chemin `/etc/myapp/settings.conf` sur notre hôte

#### Utilisation du Rôle dans le Playbook :

1. **Créez un playbook** :
   ```yaml
   ---
   - hosts: all
     become: yes
     roles:
       - basic_setup
   ```

2. **Exécution du Playbook** :
   Utilisez la commande suivante pour exécuter le playbook :
   ```bash
   ansible-playbook setup.yml
   ```

