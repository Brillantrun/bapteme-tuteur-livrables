# Remarque general

## Stucture et Organisation des fichiers

Il est important de bien organiser les packages et les classes et de suivre les normes. Les noms des packages doivent être mis en minuscule, ceux des classes en majuscule. Par exemple le package "views","controllers","models".

La bonne organisation des fichiers est primordiale pour éviter de s'induire en erreur quand on code. Ici dans le package view, le contenu du fichier teachers_edit.tpl.php est une fonctionnalité d'ajout de professeur ce  qui est une erreur fondamentale. De même dans teachers_add.tpl.php qui contient des codes qui liste les étudiants.

La bonne compréhension des attentes est aussi important que le codage, la partie lister les utilisateurs, la création et la modification de ces derniers sont des fonctionnalités utiles mais non prioritaires sur cet exercice. Bien noter les priorités fait partie de la réussite d'un bon projet.

## Fonctionnalites 

Il y a plusieurs fonctionnalites manquantes ou erronées,c'est a dire ne fonctionnent pas, dans l'application dont 
- la création, la liste, la mise à jour et la suppression de professeur
- la création, la liste, la mise à jour et la suppression d'etudiant 

# Remarque par package

## Package views

La liste des utilisateurs dans appUser_list.tpl.php est certe une fonctionnalité intéressante, cependant, il n'est pas une bonne pratique d'afficher comme cela les mots de passe des utilisateurs pour une question de sécurité, car on pourrait alors y accéder trop facilement.

## Package utils

<strong>Il ne faut pas créer des attribut de classes qu'on ne va pas utiliser</strong>. Donc, bien identifier les attributs vraiment nécessaires d'une classe. Dans la classe Database.php, on utilise pas l'attribut $dbh.

## Package models

On devrait toujours utiliser <strong> l'injection de dépendance </strong> dans les cas appropriés. Dans la classe Students.php et Teachers.php, l'instance de connexion a la base donnée donc la variable $pdo doit etre une propriété statique de la classe car elle ne change pas une fois instancier.

## Package controllers

Plusieurs fonctions inachevées et manquantes dans les contrôleurs StudentsController, TeachersController.

Il est aussi important de savoir la logique métier que de savoir utiliser le bon syntax quand on code. Dans les contrôleurs TeachersController.php, StudentsController.php, les lignes 19 et 20 , concernant l'initialisation des Students et Teachers respectivement, le syntax utilisé n'est pas correct. 

> Quand on initialise une classe, par exemple,soit la classe MyClass, le bon syntax est:
```php
$myclass= new MyClass();
```

Dans les classes TeachersController et StudentsController , on pourrait mettre "global $router" en propriété de la classe.

La fonction teachersAdd de TeachersController, lorsqu'on récupère les données depuis le formulaire d'ajout de professeur, il faut bien noter le nom de l'input en question car c'est ce dernier qu'on va récupérer dans notre contrôleur. 

- Dans notre cas, dans la fonction teachersAdd, nous récupérons une donnée qui n'existe pas depuis les "inputs" de notre formulaire : $name = filter_input(INPUT_POST, "name", FILTER_SANITIZE_SPECIAL_CHARS); Cela fera une erreur d'exécution. De même dans la fonction teachersEdit.

<<details><summary>Voici comment bien faire la liaison des données</summary>
```html
<!--partie vue-->
<input name="mydataname" value="" type="text" class="form-control">
```
```php
//recuperation
$mydata = filter_input(INPUT_POST, 'mydataname');
```
</details>

> Attention à ne pas faire des fautes de frappe, la correction des erreurs anodines comme celles peut faire perdre beaucoup de temps, comme dans SudentsController.php quand on initialise Students avec "Studentss".

Pour les fonctions existantes, <strong>il faut les nommer suivant leurs taches</strong>, dans StudentsController par exemple, nommer la fonction "studentEdit" au lieu de "teachersEdit". De même pour la <strong>nomenclature des variables qui doit être significative et claire</strong>. 

> Dans la fonction "teachersEdit", on essaie d'acceder à une variable $studentsid qui est null et qui ne vient pas en paramètre à notre fonction, par la suite la variable $studentsFromDb sera aussi null, ce qui n'est pas absolument pas cohérent et génère des erreurs à l'exécution car on essaie d'accéder à un objet null.Il faut bien s'assurer de la continuité et de la cohérence de notre code.