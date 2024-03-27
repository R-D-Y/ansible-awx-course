# Page à Pour aller plus loin...

<img src="https://i.ibb.co/GJTwyrZ/DALL-E-2024-01-15-13-11-02-An-imaginative-depiction-of-the-universe-themed-around-information-techno.png" width="600" height="600">

Malheureusement les bonnes choses ont une fin, ce chapitre signe la dernière ligne droite de ce cours.

Ce chapitre, loin d'être un simple adieu, est une invitation à poursuivre votre exploration de ce sujet, mais aussi de l'univers DevOps en continuel expansion !
 
Notre parcours jusqu'ici a été conçu comme une initiation, une découverte dans ce monde vaste des outils utilisés. Nous avons exploré les fondamentaux, compris les principes de base, et appliqué des concepts clés. Le monde de l'automatisation IT, de la conteneurisation, et de la gestion de configuration recèle de mode et technique d'utilisation plus complexes que nous n'avons fait que découvrir lors de ce cours.

Dans cette dernière section, nous vous ouvrons les portes de ce qui va au-delà du contenu de ce cours. Nous vous présenterons des techniques plus poussées, des outils alternatifs comme Podman face à avec Docker, ou encore Ansible Tower face à AWX et d'autres encore...  Nous vous présenterons à travers ce dernier chapitre des intégrations plus techniques, et des stratégies d'optimisation qui vous permettrons d'améliorer votre compréhension et compétence dans l'utilisation de ces technologies DevOps.

Concrètement, compilé à notre cours, ce dernier chapitre vous permettra de voir, et des modes de fonctionnement plus technique de ce que vous avez appris, ainsi que des technologies se rapprochant de celle du cours, de façon a en savoir davantage sur ce sujet.

 
Pour la partie "Cas d'utilisation avancés d'Ansible et d'AWX", voici un développement détaillé :

---

**Utilisation avancés d'Ansible et d'AWX**

Nous explorons des scénarios d'automatisation plus technique que vu précédemment qui démontrent la polyvalence d'Ansible et d'AWX couplé. Ces cas d'utilisation sont assez pertinents et très utiliser pour les organisations cherchant à optimiser leur gestion d'automatisation système, elles sont très fréquemment utiliser dans les grandes sociétés comme Antoine a pu le dire, mais aussi utiliser chez des SSII pour leurs clients.

1. **Gestion de configurations à grande échelle :**
   - **Contexte :** Dans les grandes entreprises comme Sanofi par exemple, la gestion de configurations pour des centaines, voire des milliers de serveurs et d'applications, Ansible est là pour standardiser et automatiser la configuration de l'ensemble de l'infrastructure (playbooks, roles, block & jobs. AWX offre à cela une interface graphique pour gérer et suivre efficacement ces automatisations de manière centralisée et industriel. Nous avons fais des exercices sur une machines Linux et une machines WIndows, mais la force d'Ansible réside dans son déploiement de masse, de ce fait, il est possible de géré des grands inventaires de plusieurs milliers de machines...

   - **Bénéfices :** Réduction des erreurs humaines, cohérence des configurations à travers l'entreprise (déploiement de masse standardisé), et évidemment un gain de temps considérable.

<img src="https://miro.medium.com/v2/resize:fit:1400/0*l5Zx0c5vJRLmZ8RL.jpg" width="600" height="600">

2. **Intégration avec des systèmes cloud :**
   - **Contexte :** Les environnements cloud, comme AWS, Azure, ou GCP, ont des besoins spécifiques en termes de gestion et d'automatisation, Évidemment, AWX permet un lien entre votre potentiel partie On-Premise et Cloud Provider.
   - **Concrètement... :** Créez des Jobs Ansible pour gérer automatiquement les ressources cloud (comme les instances VM, les réseaux, le stockage) et intégrez-les dans AWX pour une gestion centralisée, il est par exemple possible de créer des inventaires dynamique, de ce fait, en créant par exemple des machines sur AWS, avec un TAG spécifique, AWX, en étant paramétrer correctement, aura la possibilité de repérer ces tags et ainsi les rendre disponibles sur AWX afin d'y lancer des Jobs.
   - **Bénéfices :** Une efficacité dans la gestion des ressources cloud (VM, S3...) et une intégration fluide et dynamique avec l'infrastructure existante.

![image](https://github.com/R-D-Y/ansible-awx-course/assets/102509252/76399ce0-aa2a-4275-8392-5a4024a1202a)




---


---

**Faisons maintenant une comparaison entre AWX et Ansible Tower... une alternative ???**



nous examinerons ici les différences entre AWX et Ansible Tower, en discutant de leurs avantages et de leurs inconvénients. Cette comparaison vous permettra de mieux comprendre quand opter pour l'un ou l'autre outil. Sachez pour en tout cas, qu'il s'agit de 2 produits RedHat et ceux-ci restent assez similaire et fond par principe la même chose, de la gestion de configuration.

1. **AWX :**
   - **Fonctionnalités :** AWX est la version open-source d'Ansible Tower. Il offre la plupart des fonctionnalités de Tower, comme l'interface graphque, les workflows, la gestion des inventaires dynamique, la synchronisation LDAP/Github/Cloud Provider... et le contrôle d'accès basé sur les rôles.
   - **Avantages :** Gratuit et open-source, AWX est idéal pour l'expérimentation notamment pour des labs, le développement de compétences, et les environnements non critiques tel que les environnements de développement ou bien de pré-production. L'open-source favorise une personnalisation et une adaptation plus souples du produit.
   - **Inconvénients :** Comme il s'agit d'un produit open-source, il ne bénéficie pas du support officiel, ce qui est un frein considérable pour les environnements de production, aussi, certaines fonctionnalités avancées d'Ansible Tower ne sont pas disponibles sur AWX, il n'est donc pas possible d'aller aussi loin dans la technicité des infrastructures. Sa stabilité et sa fiabilité peuvent être moindres en comparaison (moins de mise à jours, corrections, mais possède une large communauté sur Github/StackOverfkow.

2. **Ansible Tower :**
   - **Fonctionnalités :** Ansible Tower est la version entreprise d'AWX proposé par RedHat. Il offre toutes les fonctionnalités d'AWX, plus des fonctionnalités avancées comme le support multi-tenant, des intégrations d'entreprise réaliser par les équipes redhat, des fonctionnalités de reporting avancées, et évidemment, un support d'entreprise.
   - **Avantages :** Avec le support d'Ansible ainsi qu'une plus grande stabilité, Tower est mieux adapté aux environnements de production. Les fonctionnalités supplémentaires facilitent la gestion à grande échelle et offrent une meilleure intégration avec d'autres outils d'entreprise, permettant de pousser la technicité des infrastructures au maximum.
   - **Inconvénients :** Ansible Tower est un produit évidemment payant, ce qui peut être un obstacle pour les petites entreprisesou bien même les admin sys souhaitant monter en compétence sur ce système. Sa nature moins ouverte peut limiter la personnalisation, il n'est pas Open-Source, vous ne faites pas ce que vous souhaiter !

<img src="https://www.eweek.com/wp-content/uploads/2020/10/Ansible-Tower-Platform-1088x725-4.png" width="600" height="600">

---


**Mais alors... j'utilise lequel et dans quelle circonstance ?????**

- **AWX**
  - Les environnements de test et de développement.
  - Expérimentation d'Ansible avec gestion de configuration et interface Graphique sans coût initial.
  - Les projets où la personnalisation open-source est essentielle.



- **Ansible Tower**
  - Les environnements de production.
  - Les organisations nécessitant un support officiel et une garantie de stabilité avec des mises à jours de sécurités perpétuels.
  - Les cas d'utilisation nécessitant des fonctionnalités avancées et une intégration poussée.

Voilà, maintenant vous savez quoi prendre !

---


---

**Parlons Intégration...**

Nous discuterons ici de l'intégration d'AWX et d'Ansible avec d'autres outils DevOps, ils en existe énormément dans cet univers,Jenkins, GitLab CI/CD, et bien d'autres... Ces derniers permettent par exemple créer des pipelines d'automatisation plus robustes et efficaces. L'intégration de ces outils joue un rôle réellement crucial dans l'orchestration des processus DevOps (push2prod), améliorant ainsi la cohérence, la vitesse et l'efficacité des opérations IT. Ils sont très utiliser dans les grandes entreprises mais nécessite une bonne compréhension de l'environnement, des bonnes pratiques et des outils afin de mettre en place ces derniers.

---
<img src="https://fiverr-res.cloudinary.com/images/q_auto,f_auto/gigs/274414624/original/af186670fa92043ff398d90aba28f0991463e545/help-you-in-kubernetes-docker-or-any-related-devops-technologie.jpeg">

---

1. **Jenkins :**
   - **Comment ça marche ?** Jenkins ( Logiciel Open-Source permettant automatiser les parties du développement logiciel) peut déclencher des jobs Ansible pour automatiser les tâches de déploiement, de test, et de gestion de configuration liées au build dans le cadre d'un pipeline CI/CD.
   - **Quoi d'plus ?** Cette intégration permet de combiner la puissance d'Ansible dans l'automatisation des configurations combiné à la flexibilité de Jenkins dans la gestion des pipelines CI/CD, cela offre un contrôle totale et une automatisation plus fine des processus de déploiement.

2. **Intégration avec GitLab CI/CD :**
   - **Comment ça marche ?** Concernant les pipelines CI/CD de GitLab (version OpenSource & local de GitHub), Ansible peut être utilisé pour exécuter des tâches d'automatisation lors de différents stades du pipeline (comme le déploiement, la mise à jour de configurations, etc.).
   - **Avantages** L'intégration d'Ansible avec GitLab CI/CD permet une gestion possiblement autonome des déploiements et des mises à jour, facilitant ainsi la livraison continue et la gestion de l'infrastructure as code, nous avons pu le voir dans les précédents exercices :) 

3. **Il en existe beaucoup d'autres...**
   - **Autres outils :** AWX/Ansible peut également s'intégrer avec d'autres outils DevOps comme Terraform, Kubernetes, des systèmes de monitoring comme Prometheus...
Ceux-ci, couplé à AWX/Ansible permettent, dans le cas où ceux-ci sont très bien maîtrisé, de maintenir un environnement de production très stable et très sécuritaire, en plus d'une possibilité d'évolution et de mise en production d'outil tierce très rapide, de façon plus claire, en maitrisant ces outils, vous pouvez faire en sorte d'avoir un énorme gain de productivité...

---
---



**Alternatives à Docker ? OUI !!!**

Dans ce monde en constante évolution de l'IT, Docker a longtemps été le standard de facto concernant la conteneurisation. Cependant, d'autres technologies ont émergé, offrant des alternatives intéressantes. Parmi elles, Podman se démarque particulièrement. Nous allons donc la comparé avec Docker, et vous en dire plus...

<img src="https://fs.buttercms.com/resize=width:885/60rkSQqZRrejdedGfkdc" width="600" height="600">

1. **Podman :**
   - **ça sert à quoi ?? :** Podman est souvent considéré comme un remplacement direct de Docker, il est en 2ème position des technologie de conteneurisation les plus en vogue. Il permet de construire, de gérer et de lancer des conteneurs sans nécessiter de daemon en arrière-plan. Podman est compatible avec les images Docker et peut souvent les exécuter sans aucune modification, Concrètement, vous n'aurez aucun mal à passer de Docker à Podman en terme d'utilisation, il vous suffit de remplacer le mot "Docker" par "podman" à chaque commande ahah! Comme dit précédemment, la seul différence est son fonctionnement (sans nécessiter de daemon).

   - **Sécurityyyy :** L'une des principales différences de Podman par rapport à Docker c'est son modèle de sécurité en effet Podman exécute chaque conteneur en tant qu'utilisateur non privilégié, réduisant ainsi les risques de sécurité liés au daemon Docker(moins de risque de sécurité), de ce fait, ce dernier va être au niveau machine, beaucoup plus sécuriser et permettrat de mieux segmenter ces derniers !
   - **Usage :** Podman est particulièrement adapté dans les environnements où la sécurité est une préoccupation (comme dans toutes entreprises je l'espère), ou pour les utilisateurs qui préfèrent une architecture sans daemon, sur le côté usage de production, le fonctionnement reste le même que partout, c'est un systeème de container.



---

**Piqure de rappel sur Docker... :**
- **Docker :**
  - **Fonctionnalités :** Docker est reconnu pour sa facilité d'utilisation, son écosystème étendu, et sa large adoption permettant d'être reconnu par une large communeauté d'utilisateurs).

  - **Sécurité :** Docker fonctionne avec un daemon central, ce qui peut présenter des risques de sécurité si le daemon est compromis, même si ce dernier s'améliore après chaque patch de sécurité.

  - **Usage :** Docker est un choix privilégié pour les développeurs et les équipes DevOps/SysOps en raison de sa communauté vaste et de son écosystème riche, offrant une grande variété d'outils et de services intégrés, en plus de ça, étant le numéro 1, il est le premier vers lequel on se tourne pour découvrir la conteneurisation.

Pour conclure, bien que Docker reste un choix populaire dans l'écosystème de la conteneurisation, des alternatives comme Podman offrent des avantages distincts en termes de sécurité et de fonctionnalités. Le choix entre Docker et podMan (même si il en existe plein d'autres tel que Swarm, rkt, LXC...)  dépendra largement des besoins spécifiques de sécurité, de l'architecture du système, et des préférences personnelles ou organisationnelles. Bien que Docker soit le numéro 1, ce dernier n'a plus le vent en poupe depuis quelques année, et pour cause, beaucoup se plaignent de certains soucis (sécurité lié au daemon, grossissement des images, difficulté en debugging...).

<img src="https://miro.medium.com/v2/resize:fit:998/0*mEH-717myKoaZPY0.png">

---
---

---

**Ressources complémentaire....**

Ce cours touche à sa fin.... Pour ceux qui cherchent à approfondir leurs connaissances en automatisation IT, en conteneurisation et même dans l'utilisation d'outils DevOps tels que Ansible, AWX, et Docker, il existe une multitude de ressources disponibles à votre porté. Nous vous proposons une liste de cours en ligne, forums, et groupes de discussion qui peuvent enrichir votre apprentissage sur le sujet et vous garder à jour avec les dernières tendances et meilleures pratiques, car oui, dans notre domaine, la veille c'est important !!


1. **Cours en ligne :**
   - **Coursera et Udemy :** Ces plateformes offrent énormément de cours couvrant Ansible, Docker, et d'autres technologies DevOps, adaptés à tous les niveaux de compétence, il vous suffira te rechercher votre sujet, et de trouver le cours qui vous correspond !
   - **Linux Academy :** Spécialisée dans les technologies open-source, Linux Academy propose des cours détaillés sur Ansible, Docker et d'autres technologies de cette univers ! (n'oubliez pas que le meilleur cours sur ce sujet c'est le notre !)

2. **Forums et Communautés :**
   - **Stack Overflow :** Un incontournable pour toute question technique, avec une communauté active et des discussions approfondies sur Ansible, Docker, et bien plus. Mais vous devez connaître la chanson !
   - **Reddit :** Les sous-forums tels que r/devops, r/ansible et r/docker sont d'excellentes sources pour des conseils, des actualités et des discussions avec d'autres professionnels. (Pour l'anecdote, c'est sur Reddit que j'ai appris le forks de Terraform en fin 2023 !). 
   - **Github:** Entre les repos public, les issues & les wikis, combinés à une très large communauté, vous trouverez sur Github beaucoup d'information de TP, de "pseudo-cours", et même des choses toutes faites qui pourrons vous servir tel que des playbook disponible en libre service !
- **Ansible Galaxy :** Vous vous en souvenez, Ansible Galaxy est un site proposé par et soutenu par Redhat afin de rendre publique et disponible des travaux & projet sur Ansible, vous y trouverez des pugins, rôles et playbook ansible proposé par la communeauté !
- **DockerHub :** Comme pour Ansible Galaxy, DockerHub est un site/plateforme permettant de déposer, ou bien récupéré du contenu (DockerFile, image de container...) proposé par la communauté, veillez tout de même a bien vérifier ce que vous télécharger, le risque 0 n'existe pas quand il s'agit de contenu communautaire. 

<a href="https://ibb.co/bNyX5tG"><img src="https://i.ibb.co/7rTKth0/Sans-titre.png" alt="Sans-titre" border="0"></a>

3. **Groupes de discussion :**
   - **Ansible et Docker Meetups :** Rejoignez des meetups locaux ou en ligne pour rencontrer d'autres professionnels et partager des connaissances et des expériences.
   - **Groupes LinkedIn et Facebook :** Ces plateformes que vous connaissez sans doutes proposent des groupes dédiés où les professionnels partagent des ressources, des conseils, et des opportunités de réseautage, parfait pour se faire de nouveaux collègues !

---

Ces ressources vous aideront non seulement à consolider vos connaissances actuelles, mais aussi à rester informé des évolutions dans le domaine de l'automatisation IT et du DevOps de manière général. La formation continue est un élément clé pour rester compétitif dans cde domaine en constante évolution.

Merci à tous !
