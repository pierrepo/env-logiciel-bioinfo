# Gérer un environnement conda avec un fichier YAML

Il est possible de décrire un environnement conda dans un fichier au format YAML.

## Exemple

Le fichier `rnaseq.yml` ci-dessous est utilisé pour construire un environnement pour l'analyse de données RNA-seq :

```
name: rnaseq
channels:
    - conda-forge
    - bioconda
    - nodefaults
dependencies:
    - fastqc
    - star>=2.6
    - samtools=1.9
```

Plusieurs sections sont présentes :

- `name` : nom de l'environnement
- `channels` : canaux qui seront utilisés pour installer les logiciels. L'ordre de ces canaux est important. Priorité est donnée au premier canal (d'abord `conda-forge` puis `bioconda`). `nodefaults` signifie que le canal par défaut par Anaconda ne sera pas utilisé.
- `dependencies` : liste des logiciels à installer. On peut préciser ou pas la version des logiciels voulues.


## Créer un environnement

```bash
$ conda env create -f rnaseq.yml
```

Le nom de l'environnement ainsi créé sera celui indiqué dans le fichier YAML (`rnaseq` dans notre exemple).

## Activer / désactiver / supprimer l'environnement.

Les commandes pour charger (activer), décharger (désactiver) et supprimer l'environnement sont les mêmes que pour un environnement créé avec `conda create` :

```bash
$ conda activate rnaseq
$ conda deactivate
$ conda remove -n rnaseq
```


## Exporter un environnement dans un fichier YAML

Il est possible d'exporter un environnement conda dans un fichier YAML :

```bash
$ conda env export -n ENVNAME > envname.yml
```

Pour des raisons de comptabilité entre machines, il est recommandé de supprimer le nom du répertoire dans lequel l'environnement a été créé (le `prefix`) et les versions très précises des logiciels (numéros de build) : 

```bash
$ conda env export -n ENVNAME --no-builds | grep -v "^prefix:" > envname.yml
```

Le fichier `envname.yml` va contenir la liste de **tous** les logiciels installés et de leurs **dépendances**. C'est parfois un peu *too much*.
Comparez par exemple les fichiers [`rnaseq.yml`](https://raw.githubusercontent.com/pierrepo/env-logiciels-bioinfo/main/cours/rnaseq.yml) et [`rnaseq_export.yml`](https://raw.githubusercontent.com/pierrepo/env-logiciels-bioinfo/main/cours/rnaseq_export.yml) obtenus par la création puis l'export de l'environnement `rnaseq` :


```bash
$ conda env create -f rnaseq.yml
$ conda env export -n rnaseq --no-builds | grep -v "^prefix:" > rnaseq_export.yml
```

Vous retrouvez les trois logiciels demandés (`fastqc`, `star` et `samtools`) mais aussi toutes les dépendances de ces logiciels (78 au total).

```{tip}
Plutôt d'exporter brutalement votre environnement Conda dans un fichier `environment.yml`, je vous conseille de le créer itérativement. C'est-à-dire qu'à chaque fois que vous avez besoin d'un nouveau logiciel, vous indiquez son nom et éventuellement sa version dans le fichier `environment.yml`, puis vous mettez à jour votre environnement avec la commande :

```bash
$ conda env update -f environment.yml
```


## Réinstaller un environnement précédemment exporté

```bash
$ conda env create -f envname.yml
```


## Partager le fichier d'environnement

Je vous conseille de versionner votre fichier d'environnement avec git et de le partager sur GitHub, avec votre code source.

Vous pouvez déposer votre fichier `environment.yml` à la racine de votre dépôt git, à côté de votre fichier `README.md`.


