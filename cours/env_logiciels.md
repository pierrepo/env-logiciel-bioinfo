# Les environnements logiciels

## Définition

```{note}
Un environnement logiciel est un ensemble de logiciels et de bibliothèques qui permettent de faire fonctionner un programme (bio)informatique.
```

L'environnement logiciel le plus immédiat est le système d'exploitation qui contient tous les logiciels nécessaires pour faire fonctionner les programmes classiques comme un navigateur web, un éditeur de code, un lecteur de musique, un tableur, etc.


## Pourquoi s'embêter avec les environnements logiciels ?

### Améliorer la reproductibilité des analyses

Dans une étude parue en 2016 dans Nature (*[1,500 scientists lift the lid on reproducibility](https://www.nature.com/articles/533452a), Baker*), 80 % des 1500 chercheurs et chercheuses interrogé.e.s indiquait qu'il y avait une « crise de la reproductibilité » en science. Cela signifie que les résultats publiés dans des articles scientifiques ne sont pas toujours reproductibles par d'autres chercheurs et chercheuses.

```{image} img/baker_nature_2016_1.jpg
:alt: Graphics "Is there a reproductibility crisis?"
:class: bg-primary mb-1
:width: 600px
:align: center
```

En biologie, 77 % des chercheurs et chercheuses interrogé.e.s indiquaient ne pas être capables de reproduire les résultats d'autres chercheurs et chercheuses. Et **60 % d'entre eux et elles indiquaient ne pas être capable de reproduire leurs propres résultats** !

```{image} img/baker_nature_2016_2.jpg
:alt: Graphics "Have you failed to reproduce an experiment?"
:class: bg-primary mb-1
:width: 600px
:align: center
```

Autant on peut comprendre que certains résultats soient difficiles à reproduire à cause de la complexité des systèmes biologiques vivants, autant il devrait être possible de reproduire presque parfaitement des analyses bioinformatiques, reposant sur des programmes informatiques.

### Les environnements logiciels

Un environnement logiciel peut être vu comme une boite virtuelle dans laquelle on installe des programmes. Ces environnements sont indispensables pour garantir la reproductibilité des analyses bioinformatiques, au même titre que d'autres solutions ou outils (versionnement du code, documentation, partage du code et des données...).

Curieusement, les environnements logiciels sont négligés. En effet, on s'assure souvent d'avoir le bon programme et les bonnes données à analyser, mais on oublie de s'assurer que l'environnement logiciel est le bon.

> “Code” is the code you care about. “Environment” is code you don’t care about.

-- Konrad Hinsen, « [A guide to reproducible research papers](https://hpc.guix.info/blog/2023/06/a-guide-to-reproducible-research-papers/) », Guix, 2023.


Dans un article publié en 2023 « [The five pillars of computational reproducibility: bioinformatics and beyond](https://academic.oup.com/bib/article/24/6/bbad375/7326135) » (Briefings in Bioinformatics, 2023), nous avons identifié cinq piliers pour améliorer la reproductibilité des analyses bioinformatiques. La maitrise de l'environnement logiciel (*Compute environment control*) est l'un de ces piliers :

```{image} img/ziemann_bib_2023.png
:alt: The five pillars of computational reproducibility.
:class: bg-primary mb-1
:align: center
```


### Un premier niveau de reproductibilité

Dans l'article « [Practical Computational Reproducibility in the Life Sciences](https://doi.org/10.1016/j.cels.2018.03.014) » (Cell Systems, 2018), les auteurs introduisent quatre niveaux de reproductibilité pour les environnements logiciels :

```{image} img/grunning_cell_systems_2018.png
:alt: Graphics "Software Stack of Interconnected Technologies that Enables Computational Reproducibility"
:class: bg-primary mb-1
:align: center
```

1. Le niveau « OS », c'est-à-dire que les logiciels sont installés à même le système d'exploitation. C'est le niveau le plus bas de reproductibilité. **À ne pas faire !**
2. Le niveau « Conda », c'est-à-dire que les logiciels sont installés dans un environnement logiciel par un outil qui s'appelle Conda, que nous verrons en détails par la suite.
3. Le niveau « Container », c'est-à-dire que les logiciels sont installés dans un conteneur logiciel, par exemple Docker ou Singularity.
4. Le niveau « VM », c'est-à-dire que les logiciels sont installés dans une machine virtuelle. C'est le plus haut niveau de reproductibilité. C'est également le plus lourd à mettre en place.

Dans ce cours, nous nous intéresserons au niveau 2, c'est-à-dire à l'utilisation de conda pour gérer les environnements logiciels. C'est un bon compromis entre simplicité et efficacité. Il faut en effet une certaine maitrise technique pour manipuler des conteneurs ou des machines virtuelles.

```{warning}
N'installer jamais de logiciel de bionformatique directement sur votre système d'exploitation (niveau 1). Vous risquez de créer des conflits avec les logiciels déjà installés sur votre système d'exploitation et de rendre votre système instable. Utilisez toujours un environnement logiciel (niveaux 2 à 4).
```

## Propriétés des environnements logiciels

L'environnement logiciel est un outil clé pour plusieurs raisons :

### Gérer les dépendances

En bioinformatique, on utilise de nombreux logiciels. Ces logiciels dépendent d'autres programmes, de langages de programmation et de bibliothèques parfois incompatibles entre eux. Par exemple le logiciel A nécessite la bibliothèque Z dans la version 1.2 alors que le logiciel B nécessite la bibliothèque Z, mais dans la version 2.3. Or, ces deux versions de la bibliothèque Z ne sont pas compatibles entre elles.

Comment faire pour installer les logiciels A et B sur la même machine ? Les environnements logiciels sont une réponse à ce problème :
- Dans un premier environnement, on installe le logiciel A avec la bibliothèque Z version 1.2.
- Dans un second environnement, on installe le logiciel B avec la bibliothèque Z version 2.3.


### Isoler les environnements

Les environnements logiciels sont la plupart du temps des boites isolées du reste du système d'exploitation. C'est-à-dire que lorsqu'on installe un programme dans un environnement logiciel, le programme n'est pas installé là où tous les autres programmes (navigateur web, traitement de texte...) sont installés, mais dans un répertoire différent, dédié à cet environnement. Cela évite ainsi de « polluer » votre système d'exploitation avec des logiciels qui ne vous servent que pour un projet particulier.

Il est recommandé de créer un environnement logiciel par projet. Cela permet de ne pas mélanger les dépendances des différents projets.


### Faciliter l'installation

Les solutions présentées ici (notamment conda) pour gérer des environnements logiciels ne nécessitent pas de droits administrateurs pour être installées. Cela signifie que vous pouvez installer ces outils de gestion d'environnement logiciel (par exemple Miniconda) sans avoir besoin de demander à un administrateur système de le faire pour vous.

Enfin, la construction des environnements virtuels ne nécessite pas non plus de droits administrateurs. Vous pouvez donc créer autant d'environnements que vous le souhaitez.

