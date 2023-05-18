# Remarque general

## Stucture et Organisation des fichiers

Il est important de bien organiser les packages et les classes et de suivre les normes. Les noms des packages doivent être mis en minuscule, ceux des classes en majuscule. Par exemple le package "views","controllers","models".

## Fonctionnalites 

Il y a plusieurs fonctionnalités manquantes ou erronées,c'est a dire ne fonctionnent pas, dans l'application dont 
- la création, la mise à jour et la suppression de professeur
- la création, la mise à jour et la suppression d'etudiant
- log in et log out

# Remarque par package

## Package views

<strong>La nomenclature des variables doit être significative et claire</strong>, mettre des noms de variables en fonction de ce qu'elles contiennent, par exemple une variable du nom de "student" doit contenir un étudiant et non un professeur. Dans le fichier students_list.tpl.php dans la boucle foreach, lorsqu'on parcourt la liste des étudiants, la variable "$currentTeacher" n'est pas appropriée.

Le formulaire d'ajout de professeur dans le fichier teachers_add.tpl.php n'est lié à aucune action, ne pas négliger l'action à laquelle se rapporte un formulaire lors de sa création. De même, d'autres formulaires comme la création et la mise à jour d'étudiant n'ont pas été créés, ainsi que la mise à jour du professeur.

## Package utils

<strong>Il ne faut pas créer des attribut de classes qu'on ne va pas utiliser</strong>. Donc, bien identifier les attributs vraiment nécessaires d'une classe. Dans la classe Database.php, on utilise pas l'attribut $dbh.

## Package models

On devrait toujours utiliser <strong> l'injection de dépendance </strong> dans les cas appropriés. Dans la classe Student.php et Teacher.php, l'instance de connexion a la base donnée donc la variable $pdo doit être une propriété statique de la classe car elle ne change pas une fois instancier.

## Package controllers

Plusieurs fonctions inachevées et manquantes dans les contrôleurs StudentsController, TeachersController.