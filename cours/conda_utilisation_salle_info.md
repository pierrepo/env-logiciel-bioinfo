# Utilisation de conda en salle informatique

Dans les salles informatiques de l'UFR Sciences du vivant, Miniconda a déjà été installé.

```{warning}
N'installez pas vous-même Miniconda dans vos sessions utilisateurs.
```

## Utiliser l'environnement d'un.e enseignant.e

Certain.e.s de vos enseignant.e.s ont déjà créé des environnements conda pour vous, ils sont immédiatement utilisables :

```bash
$ conda env list
$ conda activate ENVNAME
$ [...]
$ conda deactivate
```


## Créer votre propre environnement

```bash
$ conda env create -f envname.yml
```

Exemple :

```bash
$ conda env create -f rnaseq.yml
```

```{warning}
Nous vous rappelons que deux environnements ne peuvent pas avoir le même nom. Si besoin, vous pouvez renommer un environnement à sa création avec l'option `-n` :

```bash
$ conda env create -f rnaseq.yml -n rnaseq-env
```

```


