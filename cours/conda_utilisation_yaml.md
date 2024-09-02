# Gérer un environnement conda avec un fichier YAML

Il est possible de décrire un environnement conda dans un fichier au format YAML.

## Fichier YAML

Par exemple le fichier `rnaseq.yml` utilisé pour construire un environnement pour l'analyse de données RNA-seq :

```
name: rnaseq
channels:
    - defaults
    - bioconda
    - conda-forge
dependencies:
    - fastqc
    - star>=2.6
    - samtools=1.9
```

Plusieurs sections sont présentes :

- `name` : nom de l'environnement
- `channels` : canaux qui seront utilisés pour installer les logiciels. L'ordre de ces canaux est important. Priorité est donnée au dernier canal.
- `dependencies` : liste des logiciels à installer. On peut préciser ou pas la version des logiciels voulus.


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
Comparez par exemple les fichiers `rnaseq.yml` et `rnaseq_export.yml` obtenus par :


```bash
$ conda env create -f rnaseq.yml 
$ conda env export -n rnaseq --no-builds | grep -v "^prefix:" > rnaseq_export.yml
```

Vous retrouvez les trois logiciels demandés (`fastqc`, `star` et `samtools`) mais aussi toutes les dépendances de ces logiciels (43 au total).




## Réinstaller un environnement précédemment exporté

```bash
$ conda env create -f envname.yml
```

