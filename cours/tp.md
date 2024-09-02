# TP Conda

## Valider l'installation

Si vous utilisez votre machine personnelle, vous devez avoir installé Miniconda.
Si vous êtes dans une salle informatique de l'UFR Sciences du Vivant, Miniconda a déjà été installé pour vous.

```{tip}

⚠️ Uniquement si cela ne fonctionne pas sur les machines des salles informatiques et sur votre propre machine !

- Suivez le tutoriel [Introduction to Conda](https://astrobiomike.github.io/unix/conda-intro) du blog [Happy Belly Bioinformatics](https://astrobiomike.github.io/).
- Vous pouvez le réaliser sur votre propre machine ou sur un serveur virtuel en cliquant sur le bouton « launch binder ».

```

Vérifiez que conda est fonctionnel :

```bash
conda --version
```

Listez les environnements déjà existants :

```bash
conda env list
```

Sur votre machine personnelle, vous devriez avoir l'environnement `base` et peu ou pas d'autres environnement.

Sur les machines des salles informatiques, vous devriez avoir plusieurs environnements déjà créés.


## Explorer un environnement 

Créez l'environnement conda `rnaseq` à partir du fichier [rnaseq.yml](https://raw.githubusercontent.com/pierrepo/env-logiciel-bioinfo/main/cours/rnaseq.yml).

Chargez ce nouvel environnement.

Quelle version a été installée pour les logiciels :

- fastqc ? (`fastqc --version`)
- samtools ? (`samtools --version`)
- star ? (`STAR --version`)

Quelles sont les dernières versions disponibles dans conda ? (<https://anaconda.org/search>)


## Créer votre environnement pour le projet court

Essayez de créer un environnement conda pour votre projet court.

Pour cela :

1. Identifiez le langage de programmation que vous utiliserez.
2. Identifiez les bibliothèques associées dont vous aurez besoin.
3. Identifiez les autres logiciels dont vous aurez besoin.

Pour chacun de ces éléments, vérifiez s'il est disponible dans conda. Utilisez le moteur de recherche d'[anaconda.org](https://anaconda.org/search).

Que faire si ce n'est pas le cas ?

Créez un fichier `environment.yml` qui contient la description de votre environnement (`inspirez-vous du fichier rnaseq.yml` précédent), puis installez-le avec `conda`.

```{tip}
Dans un premier temps, ne précisez par les versions des outils que vous installez.
```

Chargez votre environnement et vérifiez que tous les langages, bibliothèques et logiciels dont vous avez besoin sont présents.

S'il manque des outils, modifiez le fichier `environment.yml` puis mettez à jour votre environnement avec la commande :

```bash
$ conda env update -f environment.yml
```

Vérifiez encore une fois que tous les outils dont vous avez besoin sont disponibles.

Déconnectez-vous de votre environnement. Vérifiez que les outils de votre projet ne sont plus disponibles. Chargez à nouveau notre environnement et vérifiez une dernière fois que tous les outils sont présents.

Déposez votre fichier `environment.yml` dans le dépôt GitHub de votre projet court.

Pensez enfin à **écrire une notice**, un fichier `README.md` (au format Markdown) qui décrira très précisément la manière de construire votre environnement conda, éventuellement d'installer les logiciels tierces non disponibles dans conda, et enfin les manières de lancer votre programme. Voici quelques exemples :

- outil [MDWS](https://github.com/MDverse/mdws/) du projet MDverse
- projet [3DGB](https://github.com/data-fun/3d-genome-builder)
- projet [BioPyAssistant](https://github.com/pierrepo/biopyassistant)
- projet [GroDecode](https://github.com/pierrepo/grodecoder)

