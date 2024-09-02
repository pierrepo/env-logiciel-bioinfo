# L'écosystème Conda 🐍

Le terme « Conda » désigne un logiciel, mais également tout un écosystème qui lui est associé.

## Anaconda

- https://www.anaconda.com/
- Distribution de conda
- Disponible pour Windows, Mac et Linux.
- **Installable sans être administrateur**.
- Très nombreux outils pour l'analyse de données (plusieurs centaines) déjà installés.
- Très bien pour les débutants.
- Pas adapté à la bioinformatique car trop de logiciels sont installés par défaut.


## Miniconda

- https://docs.conda.io/en/latest/miniconda.html
- Version light d'Anaconda (le strict minimum).
- Aussi installable sans être administrateur.
- **Recommandé pour la bioinformatique**.


## Conda

- https://docs.conda.io/projects/conda/en/latest/index.html
- [cheat sheet](https://docs.conda.io/projects/conda/en/latest/_downloads/843d9e0198f2a193a3484886fa28163c/conda-cheatsheet.pdf)
- Gestionnaire de paquets (**logiciels**) et d'**environnements**
- Installé avec Anaconda et Miniconda.
- Basé sur Python, mais peut installer R, C++, Julia...
- Liste des logiciels disponibles : https://anaconda.org/search


## Bioconda

- https://bioconda.github.io/
- Canal de diffusion de logiciels utilisés en bioinformatique (>7000 paquets).
- Utilisable par le gestionnaire de paquets conda.
- Publication : [Bioconda: sustainable and comprehensive software distribution for the life sciences](https://doi.org/10.1038/s41592-018-0046-7), Grüning et al., Nature methods, 2018.


## Schéma

```{image} img/ecosysteme_conda.png
:alt: Schéma de l'écosystème conda
:class: bg-primary mb-1
:align: center
```

- Conda est un gestionnaire de paquets et d'environnements.
- Anaconda et Miniconda sont des distributions de conda (= des moyens d'installer conda).
- Conda-forge et Bioconda sont des canaux de diffusion de logiciels (des sortes d'entrepôts).

