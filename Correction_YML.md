### Correction - Exercice 1
 
**Tâche** :
La tâche consistait à écrire un fichier YAML pour décrire un animal en utilisant une indentation appropriée pour chaque niveau d'information.

**Exemple pour le Lion** :
```yaml
animal:
  type: Mammifère
  caractéristiques:
    - Grande crinière
    - Carnivore
    - Forte et puissante
  habitat:
    - Savane
    - Régions grasses d'Afrique
```

**Explication** :
- Chaque niveau d'information est indenté par deux espaces supplémentaires par rapport au niveau précédent.
- Le nom de l'animal, "lion", est au premier niveau d'indentation.
- Les informations comme le type, les caractéristiques et l'habitat sont des clés (key) associées à leurs valeurs (value).
- Le système de clé-valeur permet de structurer les données de manière lisible et organisée.
- Les valeurs peuvent être de différents types : chaînes de caractères, listes, nombres, etc.
- Par exemple, sous la clé "caractéristiques", nous avons une liste (indiquée par le tiret "-") de caractéristiques du lion. Cela permet de représenter plusieurs valeurs pour une même clé.

-------------------------

### Correction - Exercice 2

**Tâche** :
La tâche consistait à créer un fichier YAML pour une liste de courses avec différentes catégories, en utilisant l'indentation de manière appropriée.

**Exemple concret d'une liste de courses** :
```yaml
courses:
  légumes:
    - carottes
    - épinards
    - tomates
  fruits:
    - pommes
    - bananes
    - oranges
  produits_laitiers:
    - lait
    - yaourt
  viandes:
    - poulet
    - bœuf
```

**Explication** :
- Chaque catégorie est indentée par deux espaces de plus que la catégorie parente.
- Les éléments de chaque catégorie sont indentés de deux espaces par rapport à leur catégorie parente.

-------------------------

### Correction - Exercice 3

**Tâche** :
La tâche consistait à écrire un fichier YAML pour une recette de pizza en expérimentant avec différentes indentations.

**Exemple d'une recette de Pizza** :
```yaml
recette:
  nom: Pizza Margherita
  ingrédients:
    - Pâte à pizza
    - Sauce tomate
    - Mozzarella
    - Basilic frais
    - Huile d'olive
  étapes:
    - Préchauffer le four à 220°C.
    - Abaisser la pâte à pizza sur une plaque.
    - Étaler la sauce tomate sur la pâte.
    - Répartir la mozzarella et les feuilles de basilic.
    - Arroser d'un filet d'huile d'olive.
    - Enfourner pendant 12-15 minutes, jusqu'à ce que la croûte soit dorée.
```

**Explication** :
- L'indentation est utilisée pour structurer les différentes parties de la recette (nom, ingrédients, étapes) de manière claire.
- Chaque niveau d'information est indenté de deux espaces supplémentaires par rapport au niveau précédent, créant une hiérarchie visuelle.
