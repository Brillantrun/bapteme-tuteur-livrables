# Remarque general

## Stucture et Organisation des fichiers

Il est important de bien organiser les packages et les classes et de suivre les normes. Les noms des packages doivent être mis en minuscule, ceux des classes en majuscule. Par exemple le package "views","controllers","models".

## Fonctionnalites 

Il y a plusieurs fonctionnalites manquantes ou erronées,c'est a dire ne fonctionnent pas, dans l'application dont 
- la création, la mise à jour et la suppression de professeur
- la mise à jour et la suppression d'etudiant
- log in et log out

# Remarque par package

## Package views

Il est de bonne pratique de ne pas mettre de contenus en dur dans la vue, comme la liste statique des professeurs dans student_add.tpl.php 

Dans teacher_add.tpl.php, le formulaire d'ajout de professeur n'est lié à aucune action.

En général, lorsqu'un bout de code de la partie vue,ici le contenu de la balise "head" revient à chaque affichage, ici il revient dans tous les fichiers de student et teacher: student_add.tpl.php,student_list.tpl.php,teacher_add.tpl.php,teacher_list.tpl.php. Pour éviter cette répétition, on pourrait créer dans view un dossier template ou layout par exemple dans lequel on va mettre tout ce que la balise "head" contient, de même pour un "footer", on crée deux vues header.tpl.php et footer.tpl.php. Le but est de pouvoir charger juste ces deux fichiers pour chaque contenu à afficher. Cela nous épargne de recoder a chaque fois le même code dans chaque vue.

## Package utils

<strong>Il ne faut pas créer des attribut de classes qu'on ne va pas utiliser</strong>. Donc, bien identifier les attributs vraiment nécessaires d'une classe. Dans la classe Database.php, on utilise pas l'attribut $dbh.

## Package models

On devrait toujours utiliser <strong> l'injection de dépendance </strong> dans les cas appropriés. Dans la classe Student.php, l'instance de connexion a la base donnée donc la variable $pdo doit être une propriété statique de la classe car elle ne change pas une fois instancier.

## Package controllers

Plusieurs fonctions inachevées et manquantes dans les contrôleurs StudentController, TeacherController.

Cependant, pour les fonctions existantes, <strong>il faut les nommer suivant leurs taches</strong>, dans TeacherController par exemple, nommer la fonction "addTeacher" au lieu de "studentAdd". De même pour la <strong>nomenclature des variables qui doit être significative et claire</strong>. 

- Pourtant dans la fonction "studentAdd", on initialise au début une variable $newTeacher qui devrait contenir normalement le professeur à ajouter, alors que par la suite ce variable n'est plus du tout utilisée, par contre on utilise dans les codes suivants une variable non initialisée nommée $newStudent, ce qui n'est pas absolument pas cohérent et génère des erreurs à l'exécution car on essaie d'accéder à un objet null.