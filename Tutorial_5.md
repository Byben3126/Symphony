
# Transformer en API en Server-Side Rendering

1. [Prérequis](#1--Prérequis)
2. [Server-Side Rendering c'est quoi](#2--Server-Side-Rendering-c'est-quoi)
3. [Partage du projet Symphony](#3--Partage-du-projet-Symphony)
4. [Transforamation de notre route /users](#4--Transforamation-de-notre-route-/users)

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
Lors de l'initialisation du projet symfony en format webapp vous avez pu remarquer l'ajout d'un dossier template :
base.html.twig se trouvant a l'interieur de celui-ci. Le role de notre controller est de renvoyer le nom du fichier
twig et également les données nécessaire a la creation du fichier twig.

Twig est un moteur de templates pour le langage de programmation PHP, utilisé par défaut par le framework Symfony.
Il a une syntaxe differente à php, et rend la lecture de l'html facile

La methode render permet de retouner au client une vue html, elle prend en argument le nom du fichier
twig et les données nécessaire a la creation du fichier twig.

```php
#[Route('/users', name: 'app_users')]
public function index(UsersRepository $UsersRepository): JsonResponse
{
    $users = $UsersRepository->findAll();
    return $this->render('user/index.html.twig', [
            'users' => $users,
    ]);
}
```

## 4 | Création du fichier twig
Nous devons maintenant coder le fichier index.html.twig

```twig
{# user/index.html.twig #}

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>User List</title>
</head>
<body>

    <h1>User List</h1>

    <table border="1">
        <thead>
            <tr>
                <th>ID</th>
                <th>First Name</th>
                <th>Email</th>
            </tr>
        </thead>
        <tbody>
            {% for user in users %}
                <tr>
                    <td>{{ user.getId() }}</td>
                    <td>{{ user.getFirstName() }}</td>
                    <td>{{ user.getEmail() }}</td>
                </tr>
            {% endfor %}
        </tbody>
    </table>

</body>
</html>
```
Dans ce code, nous utilisons une boucle Twig ({% for user in users %}) pour itérer à travers la liste des utilisateurs et afficher leurs informations. Les méthodes dans Twig (getId(), getFirstName(), getEmail()) correspond à ceux définis dans notre entité Users.
