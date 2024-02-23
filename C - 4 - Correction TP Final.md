Dans un premier temps, rendez-vous sur Github afin d'ajouter le windows server dans l'inventaire. Bien évidemment avec les commandes Git ! 

Changement à faire dans le fichier inventory.ini : 

![Capture d’écran 2024-02-14 111458](https://github.com/0xAntoineB/My_first_repo/assets/80824417/05773d58-02bf-421b-839a-3025a5573965)

Commandes Git à faire : 

```
git add inventory.ini
```

```
git commit -m "Ajout du serveur windows dans l'inventaire"
```

```
git push 
```

Développement !! Je vous donne le playbook pour créer l'utilisateur sur l'ad et l'ajouter dans le groupe qui va bien 

![Capture d’écran 2024-02-14 111220](https://github.com/0xAntoineB/My_first_repo/assets/80824417/4b1d6930-fdd1-41c8-ba81-1b5bac0a8241)

Vous avez modifié votre inventaire puis créer un playbook, n'oubliez pas de re synchroniser le projet pour que la modification des fichiers soit prise en compte !

Il va falloir maintenant recréer le playbook puis le lancer dans AWX, rendez-vous dans l'onglet modèle : 

![Capture d’écran 2024-02-14 111315](https://github.com/0xAntoineB/My_first_repo/assets/80824417/48f2f82c-2ea2-496b-9199-019562a4d03f)

!! N'oubliez pas d'allumer le serveur et de vous connectez user/motdepasse !! 

Une fois l'utilisateur créé, on redéveloppe ! Trouver trois paquets de votre choix à installer sur le serveur node ! Pour ma part j'ai repris le premier playbook : 

![Capture d’écran 2024-02-23 094612](https://github.com/0xAntoineB/My_first_repo/assets/80824417/67a7b1fe-60d8-431c-9902-b3f88efb858a)

Il faut l'ajouter maintenant dans votre GitHub, avec les commandes :) 

```
git add paquets.yml #le nom de votre nouveau fichier
```

```
git commit -m "Ajout fichier des paquets"
```

```
git push 
```

Bien évidement, n'oubliez pas de resynchroniser le projet ! Puis on va recréer le playbook dans l'onglet modèle : 

![Capture d’écran 2024-02-23 095600](https://github.com/0xAntoineB/My_first_repo/assets/80824417/b2fe469e-6b22-4b88-b1c0-c75dee277484)

On va donner des permissions à notre nouveau utilisateur afin qu'il puisse taper sur le nouveau fichier de packages, rendez-vous dans l'onglet utilisateur -> newuser -> permissions : 

![Capture d’écran 2024-02-14 120839](https://github.com/0xAntoineB/My_first_repo/assets/80824417/a5726522-b016-478c-beda-9cd82e1f8d82)

On ensuite va update le fichier d'inventaire en ajoutant le serveur node si c'est pas déjà fait ! 

![Capture d’écran 2024-02-14 110740](https://github.com/0xAntoineB/My_first_repo/assets/80824417/8e0bc611-2355-4276-a6cb-0eeaf5c2372d)

Avec les commandes git ! Puis on resynchronise 

On peut ensuite se connecter avec notre nouvel utilisateur de l'AD sur la plateforme. 

Puis on créer une planification, rendez-vous sur le playbook -> planification. Changer la date et l'heure en fonction de vous :) : 

![Capture d’écran 2024-02-23 090743](https://github.com/0xAntoineB/My_first_repo/assets/80824417/27b595e4-31d4-4fe6-a4f9-fe1b485e7c7a)

Une fois ça, reconnectez vous en admin et puis visualiser votre playbook qui va se lancer :) 

ET VOILA ! Vous avez réussi le final boss des TP ! 

Facile ! C'est les bases, nous allons maintenant vous fournir des autres façons de penser pour aller plus loin, mais vous serez guider seul dans votre apprentissage car nous aurons pas le temps de vous en apprendre plus. 

Le cœur du sujet se termine ici, merci d'avoir pris le temps :) 

