# Installation & Initialisation d'un projet Symphony

1. [Prérequis](#1--Prérequis)
2. [Installation](#2--Installation)
3. [Partage du projet Symphony](#3--Partage-du-projet-Symphony)
4. [Les commandes utilies](#4--Commandes-utiles)

## 1 | Prérequis

Assurez-vous de satisfaire les conditions suivantes avant d'installer Symfony 7 :

1. PHP : Symfony 6 nécessite PHP 8.0. Vous pouvez vérifier votre version de PHP en exécutant la commande suivante dans votre terminal :

  ```bash
  php --version
  ```
Si vous avez une version antérieure à PHP 8.0, vous devrez mettre à jour PHP.

2. Composer : Symfony utilise Composer pour la gestion des dépendances. Installez Composer en suivant les instructions sur getcomposer.org.

```bash
composer --version
```
Cette commande permet de verififer si composer et bien installer et accessible.

3. Installer Symfony CLI. Il fournit tous les outils dont vous avez besoin pour développer et gérer votre Application de Symfony localement.

Windows avec [Scoop](https://scoop.sh/)
```bash
scoop install symfony-cli
```

Mac OS/Linux avec [Homebrew](https://brew.sh/)
```bash
brew install symfony-cli/tap/symfony-cli
```

4. Vérifier si votre ordinateur rencontre des exigences supplémentaire grace à Symfony CLI
```bash
symfony check:requirements
```


## 2 | Installation

Ouvrez votre terminal et exécutez n'importe laquelle de ces commandes pour créer un nouveau Symfony application: :

Pour un projet web
```bash
symfony new my_project_directory --version="7.0.*" --webapp
```

Pour une simple instalation backend
```bash
symfony new my_project_directory --version="7.0.*"
```

La seule différence entre ces deux commandes est le nombre de paquets installé par défaut. Le --webappoption installe tous les paquets que vous ont généralement besoin de construire des applications web, de sorte que la taille de l'installation sera plus grande.

## 3 | Partage du projet Symphony

L'avantage du frameword synfony et de pouvoir deployer le projet sur un grand nombre de poste de travail en tres peu de temps;

```bash
git clone ...
cd my-project/
composer install
```
Dans cet exemple nous prenons un projet symphony deja existant et deployer sur un repository git
Nous verions la suis des commande à executer dans le chapitre de L'orm de Symphony

## 4 | Commandes utiles

Instalation des packages pour un connexion à une base de donnée
```bash
php bin/console cache:clear
composer install
composer require symfony/orm-pack
composer require --dev symfony/maker-bundle
symfony console doctrine:database:create
```

Creation d'une entity
```bash
php bin/console make:entity
```

Creation des fichier sql des entity
```bash
php bin/console make:migration
```
Migration dans la Base de donnée
```bash
php bin/console doctrine:migrations:migrate
```

