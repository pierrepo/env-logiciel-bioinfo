# Utilisation de conda

## Gérer les logiciels

### Chercher un logiciel

```bash
$ conda search jupyterlab
Loading channels: done
# Name                       Version           Build  Channel             
jupyterlab                    0.27.0  py27h42ebfef_2  pkgs/main           
jupyterlab                    0.27.0  py35h29561ed_2  pkgs/main           
jupyterlab                    0.27.0  py36h86377d0_2  pkgs/main           
jupyterlab                    0.30.4          py27_0  pkgs/main           
jupyterlab                    0.30.4          py35_0  pkgs/main
[...]
```

On obtient une liste des versions disponibles pour le logiciel `jupyterlab`.

On peut également chercher un logiciel dans un canal spécifique :

```bash

Chercher un logiciel dans un canal spécifique :

```bash
$ conda search -c bioconda hisat2
Loading channels: done
# Name                       Version           Build  Channel             
hisat2                     2.0.0beta          py27_0  bioconda            
hisat2                     2.0.0beta          py34_0  bioconda            
hisat2                     2.0.0beta          py35_0  bioconda            
hisat2                     2.0.1beta          py27_0  bioconda            
hisat2                     2.0.1beta          py34_0  bioconda  
```

La recherche peut également se faire en ligne, sur le site <https://anaconda.org/search>.


### Installer un logiciel

```bash
$ conda install jupyterlab
```

En spécifiant un canal quand c'est nécessaire :

```bash
$ conda install -c bioconda hisat2
```

```{note}
1. Il n'est pas nécessaire d'être administrateur de la machine pour installer des logiciels avec conda.
2. **N'installez pas de logiciel en dehors d'un environnement conda dédié**. En particulier, n'installez rien dans `base` qui est l'environnement par défaut de conda.
```

### Supprimer un logiciel

```bash
$ conda remove jupyterlab
```

## Gérer les environnements

### Créer un environnement

```bash
$ conda create -n test-env
```

```{warning}
Deux environnements ne peuvent pas avoir le même nom.
```

### Charger (activer) un environnement

```bash
$ conda activate test-env
```

Votre *prompt* (invite de commande) est modifiée lorsque vous activez un environnement conda :

```bash
(base) pierre@vanille:~$ echo "hello"
hello
(base) pierre@vanille:~$ conda activate test-env
(test-env) pierre@vanille:~$ echo "hello"
hello
```

À gauche, votre prompt passe de `(base)` à `(test-env)`.

Le prompt est modifié pour vous indiquer dans quel environnement vous êtes.


### Quitter (désactiver) un environnement

```bash
$ conda deactivate
```

Ici encore le prompt est modifié et revient à `(base)` : 

```bash
(test-env) pierre@vanille:~$ conda deactivate
(base) pierre@vanille:~$ 
```


### Lister les logiciels installés dans l'environnement courant

```bash
$ conda list
```

### Lister les environnements existants

```bash
$ conda env list
```

```{tip}
Il est tout à fait normal (et même recommandé) d'avoir plusieurs environnement conda sur votre machine. Idéalement, vous devriez avoir au moins un environnement par projet.

**Un projet = un environnement**
```

### Supprimer un environnement

```bash
$ conda env remove -n test-env
```
