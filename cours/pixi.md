# Pixi

L'utilisation de conda et Miniconda pose plusieurs problèmes :

1. L'utilisation de Miniconda est autorisé pour des fins d'enseignement et de recherche, mais Anaconda met de plus en plus la pression sur des organismes de recherche pour qu'ils achètent des licences.
2. L'installation de paquets via conda peut parfois être encore lente.
3. Il n'est pas possible de lancer un outil installé dans un environnement conda sans avoir chargé l'environnement au préalable.

[Pixi](https://pixi.sh) est un projet open source écrit en Rust (donc ultra rapide) qui vise à résoudre ces problèmes.


## Installer

https://pixi.sh/latest/

- Pixi est disponible pour Linux, Mac et Windows et il n'est pas nécessaire d'être administrateur pour l'installer.
- Pixi n'est composé que d'un seul fichier exécutable.
- Pixi peut installer n'import quel logiciel disponible dans conda ou PyPI.


## Créer un environnement

Pixi n'utilise les mêmes fichiers de description d'environnement que conda, mais il est possible de les importer dans Pixi :

```bash
pixi init ---import rnaseq.yml
```

Un fichier `pixi.toml` est créé :

```toml
[project]
authors = ["Pierre Poulain <pierre.poulain@cupnet.net>"]
channels = ["conda-forge", "bioconda", "nodefaults"]
description = "Add a short description here"
name = "rnaseq"
platforms = ["linux-64"]
version = "0.1.0"

[tasks]

[dependencies]
fastqc = "*"
star = ">=2.6"
samtools = "1.9.*"
```

Il reprend toutes les caractéristiques du fichier `rnaseq.yml` initial.

```{warning}
Pixi installe les logiciels dans un répertoire caché dans le répertoire courant. Il n'est pas donc possible de n'avoir qu'un seul environnement Pixi dans un répertoire donnée.
```

## Utiliser

Pixi est très pratique, car on peut exécuter une commande dans l'environnement à la volée, sans charger explicitement l'environnement au préalable :

```bash
$ pixi run samtools --version
samtools 1.9
Using htslib 1.9
Copyright (C) 2018 Genome Research Ltd.
```

L'exécution de la commande précédente a pris quelques secondes, car Pixi a d'abord créé l'environnement, installé les logiciels et leurs dépendances, puis exécuté la commande `samtools --version`.

Si vous relancez la commande précédente, elle sera exécutée instantanément, car l'environnement est déjà créé.

On peut également charger l'environnement pour exécuter plusieurs commandes :

```bash
$ pixi shell
$ samtools --version
18:57 $ samtools --version
samtools 1.9
Using htslib 1.9
Copyright (C) 2018 Genome Research Ltd.
$ STAR --version
2.7.10b
$ exit
```

La commande `pixi shell` ouvre un shell dans l'environnement créé par Pixi. On peut exécuter autant de commandes que l'on veut dans cet environnement. La commande `exit` permet de quitter l'environnement.

N'hésitez pas explorer plus en détail Pixi :

- La rubrique « [Basic Usage](https://pixi.sh/latest/basic_usage/) » de la documentation de Pixi.
- L'article de blog « [7 Reasons to Switch from Conda to Pixi](https://prefix.dev/blog/pixi_a_fast_conda_alternative) ».
- L'article de blog « [Reproducible Notebooks with Pixi](https://prefix.dev/blog/pixi_jupyter_notebooks) ».
- L'article de blog « [Pixi - reproducible, scientific software workflows!](https://prefix.dev/blog/pixi_for_scientists) ».
