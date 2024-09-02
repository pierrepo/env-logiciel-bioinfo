# Conclusion

## Que faire si un logiciel n'est pas disponible dans conda ?

La disponibilité d'un logiciel dans Conda (plus précisément dans un canal) implique que le développeur a « packagé » ce logiciel spécifiquement pour Conda.

Si le logiciel est un paquet Python non disponible pour Conda, mais disponible dans [PyPI](https://pypi.org/), vous pouvez l'installer avec la directive `pip` dans le fichier YAML. C'est par exemple le cas pour le programme [PBxplore](https://github.com/pierrepo/PBxplore) :

```yaml
name: pbxplore
channels:
    - conda-forge
    - nodefaults
dependencies:
    - python
    - pip
    - pip:
        - weblogo
        - pbxplore
```

La première mention de `pip` indique qu'il faut installer `pip` dans l'environnement conda. La seconde mention de `pip` (avec les `:`) spécifie les paquets Python à installer avec `pip`, ici `weblogo` et `pbxplore`. Notez que les paquets Python à installer par `pip` sont marqués par une indentation (un décalage vers la droite) supplémentaire.

Enfin, si le programme qui vous intéresse n'est pas un logiciel Python dans PyPI, vous pouvez :

- Utiliser [`BiocManager`](https://www.bioconductor.org/install/) pour les paquets Bioconductor en R. Notez que la plupart des paquets Bioconductor sont déjà disponibles dans conda.
- Compiler le logiciel à installer depuis les sources avec les traditionnelles commandes `make` et `make install`. C'est très fastidieux.
- Utiliser le logiciel d'installation de votre système d'exploitation (par exemple `apt` pour Ubuntu, `brew` pour MacOS). C'est parfois indispensable pour certaines bibliothèques systèmes. Mais attention à la casse. Par ailleurs, cette méthode ne sera possible que sur une machine dont vous avez les droits administrateur.

```{note}
Les conteneurs de type Docker ou Singularity sont aussi d'excellentes solutions pour créer des environnements logiciels isolés. Mais ils ne répondent pas à la question de l'installation des logiciels, sauf si vous utilisez une image déjà construite avec le logiciel que vous cherchez.
```

## Bilan

- Utilisez **toujours** des environnements logiciels (projets, stages...).
- **1 projet = 1 environnement**.
- N'installez rien dans l'environnement par défaut, `base`, de Conda.
- Décrivez vos environnements dans des fichiers yaml (`environment.yml` par exemple).
- Versionnez ces fichiers yaml (git / Github).

Enfin, osez expérimenter et tester. Maitriser son environnement logiciel est une compétence indispensable en bioinformatique.

```{image} img/it_s_alive.gif
:alt: It's alive!
:class: bg-primary mb-1
:align: center
```


## Références, pour aller plus loin

- [Conda le meilleur ami du bioinformaticien](https://bioinfo-fr.net/conda-le-meilleur-ami-du-bioinformaticien). Article d'introduction. Attention cependant, certaines commandes sont obsolètes.
- [Comment fixer les problèmes de déploiement et de durabilité des outils en bioinformatique ? Indice : conda !](https://bioinfo-fr.net/comment-fixer-les-problemes-de-deploiement-et-de-durabilite-des-outils-en-bioinformatique). Article un peu plus technique.
- [An introduction to Conda](https://astrobiomike.github.io/unix/conda-intro), Happy Belly Bioinformatics.
- Vidéo « [The only CONDA tutorial you'll need to watch to get started](https://www.youtube.com/watch?v=sDCtY9Z1bqE) », Coding Professor, 2021.