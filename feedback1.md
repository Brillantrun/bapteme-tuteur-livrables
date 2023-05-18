# Remarque générale

## Structure et Organisation des fichiers

Il est important de bien organiser les packages et les classes et de suivre les normes. Les noms des packages doivent être mis en minuscule, ceux des classes en majuscules. Par exemple le package "views","controllers","models".

# Remarque par package

## Package utils

<strong>Il ne faut pas créer des attributs de classes qu'on ne va pas utiliser</strong>. Donc, bien identifier les attributs vraiment nécessaires d'une classe. Dans la classe Database.php, on n'utilise pas l'attribut $dbh.

## Package models

Dans le développement Oriente objet, comme son nom l'indique, il faut identifier les entités clés qui vont être souvent utilises dans nos codes et en créer des classes pour éviter la répétition des lignes de code.

On devrait toujours utiliser <strong> l'injection de dépendance </strong> dans les cas appropries. Dans la classe AppUser.php par exemple, l'instance de connexion à la base donnée donc la variable $pdo doit être une propriété statique de la classe car elle ne change pas une fois instancier. De même dans les classes Student.php, Teacher.php.

## Package controllers

<strong>Ne jamais mettre des codes mortes, c'est a dire les codes qui sont commentés.</strong>
Comme dans les classes [CoreController](bapteme_php/apprenant1/app/Controllers/CoreController.php), [StudentController](bapteme_php/apprenant1/app/Controllers/StudentController.php).

Les commentaires doivent être distincts et clairs pour chaque fonction, pour ne pas confondre ce qu'elles font exactement comme dans StudentController ou les deux fonctions studentUpdateGet, studentUpdatePost qui ont tous les deux des mêmes commentaires "edit a student".

``` txt
- Ici par exemple on pourrait mettre en commentaire pour studentUpdateGet, "show edit student form"
- Et pour studentUpdatePost reste "edit a student"
```

- De même pour les fonctions studentAddGet et studentAddPost. Cela facilitera la lecture de la documentation de l'application car l'ambiguïté des commentaires pourrait induire en erreur l'utilisateur ou un autre développeur qui pourrait reprendre le projet.

Toujours pour les commentaires, il est de bonne pratique de mettre les commentaires en une seule langue de notre choix, soit en français, soit en anglais par exemple car la génération de la documentation de l'application se fera à partir de ces commentaires. On aura de cette manière une documentation uniforme. Ce cas se présente dans les classes StudentController, TeacherController et UserController.

Dans la classe UserController, on pourrait mettre "global $router" en propriété de la classe.

Dans la classe StudentController et TeacherController, ce serait une bonne pratique d'injecter les classes de dépendances Student et Teacher, respectivement. Cela permet par la suite de faire appel à toutes les fonctions dont nous aurons besoin lors de la création, mise a jour ou suppression d'un étudiant ou d'un professeur selon l'action en cours. Comme lorsque nous appelons "$newstudent->find($studentid);" par exemple.

La richesse du développement orienté objet est également le fait d'avoir un code bien organisé et concis au niveau des classes. Il est alors important de savoir <strong>la bonne essence des setters et des getters</strong>. Pour une quelconque propriété, c'est au niveau setters qu'on doit mettre tous les contrôles de valeurs possibles comme la vérification si c'est vide par exemple. Donc dans les classes StudentController et TeacherController, la gestion des erreurs concernant les attributs de Student et Teacher,respectivement, comme "firstname", "lastname" et les autres attributs devraient se faire au niveau classe pour une bonne pratique. 

- Cela n'empeche pas, tout de même, de faire une vérification spécifique au niveau contrôleur s'il y en a, mais dans le cas où le contrôle en question est assez général ou pourrait concerner presque toutes les instances de la classe en question, il est mieux de le mettre niveau setters.