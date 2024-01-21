
# Transformer en API en Server-Side Rendering

1. [Prérequis](#1--Prérequis)
2. [Installation](#2--Installation)
3. [Partage du projet Symphony](#3--Partage-du-projet-Symphony)
4. [Les commandes utiles](#4--Commandes-utiles)

## 1 | Prérequis
1. Il est important d'avoir regardé les tutoriels précédents
2. D'avoir initialisé le projet en webapp
```bash
symfony new my_project_directory --version="7.0.*" --webapp
```
Le but est de transformé notre petite api en Server-Side Rendering, à la fin de ce tutoriel il ne sera plus question d'API

## 2 | Server-Side Rendering c'est quoi

Le rendu côté serveur d'une page web ou Server Side Rendering (SSR) est une technique de développement web qui consiste à créer les pages html côté serveur pour les envoyer toutes faites au navigateur. 


## 3 | Transforamation de notre route /users

Voici la fonction actuelle executée apres l'appel de cette route (/users)
```php
#[Route('/users', name: 'app_users')]
public function index(UsersRepository $UsersRepository): JsonResponse
{
    $users = $UsersRepository->findAll();
    return $this->json($users,200, [], ['groups' => 'getUser']);
}
```
Le but de la transformation est de renvoyer au client une page Html contenant la liste des utilisateurs

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


### 1. Entity et base de donnée

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

### 2. Serveur

Lancement du serveur symfony
```bash
symfony server:start 
```

### 3. Fixture

Création de jeu de test
```bash
composer require orm-fixtures --dev
php bin/console make:fixtures

php bin/console doctrine:fixtures:load
```
