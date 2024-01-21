# Installation & Initialisation d'un projet Symfony

1. [Prérequis](#1--prérequis)
2. [Installation](#2--installation)
3. [Partage du projet Symfony](#3--partage-du-projet-symfony)

## 1 | Prérequis

Assurez-vous de satisfaire les conditions suivantes avant d'installer Symfony 7 :

1. **PHP :** Symfony 7 nécessite PHP 8.0. Vous pouvez vérifier votre version de PHP en exécutant la commande suivante dans votre terminal :

    ```bash
    php --version
    ```

   Si vous avez une version antérieure à PHP 8.0, vous devrez mettre à jour PHP.

2. **Composer :** Symfony utilise Composer pour la gestion des dépendances. Installez Composer en suivant les instructions sur [getcomposer.org](https://getcomposer.org/).

    ```bash
    composer --version
    ```

   Cette commande permet de vérifier si Composer est bien installé et accessible.

3. **Installer Symfony CLI :** Il fournit tous les outils dont vous avez besoin pour développer et gérer votre application Symfony localement.

   - **Windows avec [Scoop](https://scoop.sh/):**
     ```bash
     scoop install symfony-cli
     ```

   - **Mac OS/Linux avec [Homebrew](https://brew.sh/):**
     ```bash
     brew install symfony-cli/tap/symfony-cli
     ```

4. **Vérifier si votre ordinateur répond aux exigences supplémentaires grâce à Symfony CLI:**
    ```bash
    symfony check:requirements
    ```

## 2 | Installation

Ouvrez votre terminal et exécutez l'une de ces commandes pour créer un nouveau projet Symfony :

- **Pour un projet web :**
    ```bash
    symfony new my_project_directory --version="7.0.*" --webapp
    ```

- **Pour une simple installation backend :**
    ```bash
    symfony new my_project_directory --version="7.0.*"
    ```

   La seule différence entre ces deux commandes est le nombre de paquets installés par défaut. L'option `--webapp` installe tous les paquets dont vous avez généralement besoin pour construire des applications web, ce qui entraînera une installation plus volumineuse.

## 3 | Partage du projet Symfony

L'avantage du framework Symfony est la possibilité de déployer le projet sur un grand nombre de postes de travail en très peu de temps :

```bash
git clone ...
cd my-project/
composer install

Dans cet exemple, nous prenons un projet Symfony déjà existant et le déployons sur un dépôt Git. Nous verrons la suite des commandes à exécuter dans le chapitre de l'ORM de Symfony.
