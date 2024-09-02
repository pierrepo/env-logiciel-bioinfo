# Environnements logiciel pour la bioinformatique

## Compiler le cours dans un environnement conda

Installer [miniconda(https://docs.anaconda.com/miniconda/index.html)] ([tutoriel pour l'installation officiel](https://python.sdv.u-paris.fr/annexe_B_install_python/))

Créer l'environnement conda :

```bash
conda env create -f environment.yml
```

Charger l'environnement :

```bash
conda activate env-logiciel-bioinfo
```

Compiler le cours avec [Jupyter Book](https://jupyterbook.org/en/stable/intro.html) :

```bash
jupyter-book build cours
```

La version HTML du cours se trouve dans le répertoire `cours/_build/html/index.html`.


## Compiler le cours dans un environnement Pixi


Installer [Pixi](https://pixi.sh/latest/).

```bash
$ pixi run compile
```
