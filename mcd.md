# Correction MCD

## Correction

- Une commande ORDER peut contenir 1 ou plusieurs produits PRODUCT, comme dans l'énoncé qui dit: "Il peut aussi bien sur passer une commande sur un produit"
- Et un produit peut être dans une ou plusieurs commandes. Donc la relation entre ORDER et PRODUCT est "plusieurs à plusieurs"
> Donc une relation "plusieurs à plusieurs" déduit une autre table qu'il faut créer à part qu'on pourrait appeler dans notre cas <strong>ORDER_PRODUCTS</strong> qui regroupe plusieurs lignes de combinaison formée par idOrder-idProduct,tous les deux étants de clés étrangères

- La relation entre USER et PRODUCT egalement doit etre "plusieurs à plusieurs", compte tenu du fait qu'un utilisateur peut "liker" un ou plusieurs produits , de même un produit peut "liker" par un ou plusieurs utilisateurs
> On devrait en déduire une table <strong>PRODUCT_LIKES</strong> qui regroupe plusieurs lignes de combinaison formée par idProduct-idUser, tous les deux étants de clés étrangères

## Recommendation

Voici quelques exemples d'outils pour realiser des MCD pour la prochaine fois:
- Visual Paradigm Community Edition, il propose une version gratuite avec des fonctionnalités avancées pour la modélisation des données.
- SQL Power Architect propose egalement une version gratuite qui est la Community Edition, elle propose egalement des fonctionnalités poussées pour la conception et la modélisation de bases de données.