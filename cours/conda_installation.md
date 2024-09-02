# Installation de conda

Dans le cadre d'un travail de bioinformatique, nous vous conseillons d'installer [**Miniconda**](https://docs.conda.io/en/latest/miniconda.html).

⚠️ Beaucoup de logiciels de bioinfo dans Bioconda ne sont disponibles que pour Mac et Linux.

Par exemple :

- [star](https://anaconda.org/bioconda/star)
- [bowtie2](https://anaconda.org/bioconda/bowtie2)
- [gromacs](https://anaconda.org/bioconda/gromacs)

Observez les badges verts : « linux-64 », « osx-64 », « linux-aarch64 » ou « osx-arm64 » qui indiquent que ces logiciels sont installables sur des systèmes d'exploitation Linux et Mac OSX.

Cependant, il existe quelques logiciels également disponibles pour Windows, par exemple :

- [fastqc](https://anaconda.org/bioconda/fastqc)

Le badge vert « noarch » indique que ce logiciel est installable sur n'importe quel système d'exploitation.

## Installer Miniconda sur une machine personnelle

Sur votre machine personnelle, il est indispensable d'installer Miniconda dans un système de type Linux (au sens large). Voici quelle version choisir sur le site de Miniconda :

- Windows 10/11 ➡️ Windows Subsystem for Linux (WSL) ➡️ Linux : « Miniconda3 Linux 64-bit »
- Linux ➡️ Linux : « Miniconda3 Linux 64-bit »
- MacOSX ➡️ macOS : choisir la bonne version du processeur (Intel ou Apple M1)


```{tip}
Vous trouverez des conseils pour installer WSL sur la rubrique [Linux](linux).
```


## Miniconda dans les salles informatiques

Dans les salles informatiques de l'UFR Sciences du Vivant, Miniconda est déjà installé. Vous pouvez donc l'utiliser directement. Vous disposez a priori d'une version récente :

```bash
$ conda --version
conda 24.5.0
```

```{warning}
**N'installez pas miniconda dans vos sessions utilisateurs** sur les machines des salles informatiques. Cela va créer des conflits avec les versions déjà installées et engorger inutilement votre espace utilisateur.

```{image} img/i_see_you.gif
:alt: I see you!
:class: bg-primary mb-1
:align: center
```

```

