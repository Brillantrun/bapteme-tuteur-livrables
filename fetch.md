# Fetch: la methode JavaScript 

## C'est quoi la notion "Fetch"

La notion "fetch" en JavaScript fait référence à la fonction 'fetch()' elle même. Cette dernière est utilisée pour effectuer des requêtes réseau (HTTP) afin de récupérer des ressources à partir d'une URL spécifiée.Elle est utilisée pour effectuer des requêtes asynchrones et recevoir des réponses au format JSON, texte, HTML ou tout autre format pris en charge par le navigateur.
> Pour faire court, cette méthode permet l’échange de données avec le serveur de manière asynchrone.

## Comment cela fonctionne-t-il?

La méthode fetch() prend en unique argument obligatoire le chemin de la ressource qu’on souhaite récupérer. On va également pouvoir lui passer en argument facultatif un liste d’options sous forme d’objet littéral pour préciser la méthode d’envoi, les en-têtes, etc.

La méthode fetch() renvoie une promesse (un objet de type Promise) qui va se résoudre avec un objet Response. Notez que la promesse va être résolue dès que le serveur renvoie les en-têtes HTTP, c’est-à-dire avant même qu’on ait le corps de la réponse.

La promesse sera rompue si la requête HTTP n’a pas pu être effectuée. En revanche, l’envoi d’erreurs HTTP par le serveur comme un statut code 404 ou 500 vont être considérées comme normales et ne pas empêcher la promesse d’être tenue.

On va donc devoir vérifier le statut HTTP de la réponse. Pour cela, on va pouvoir utiliser les propriétés ok et status de l’objet Response renvoyé.

La propriété ok contient un booléen : true si le statut code HTTP de la réponse est compris entre 200 et 299, false sinon.

La propriété status va renvoyer le statut code HTTP de la réponse (la valeur numérique liée à ce statut comme 200, 301, 404 ou 500).

## Exemple simple de son utilisation

```js
    fetch('https://mon-url.com/data')
    .then(response => {
        // Traitement de la réponse
        if (response.ok) {
            return response.json(); // Convertit la réponse en JSON
        }
        throw new Error('Erreur de réseau');
    })
    .then(data => {
        // Utilisation des données
        console.log(data);
    })
    .catch(error => {
        // Gestion des erreurs
        console.error('Une erreur s\'est produite', error);
    });
```
```txt
- Dans cet exemple, fetch('https://mon-url.com/data') envoie une requête GET à l'URL spécifiée. La réponse est gérée par la première fonction de rappel dans then(). Si la réponse est réussie (statut HTTP 200-299), nous utilisons response.json() pour convertir la réponse en format JSON.
- Ensuite, nous utilisons la deuxième fonction de rappel then() pour traiter les données résultantes. Dans cet exemple, nous affichons simplement les données dans la console.
- Si une erreur se produit à n'importe quelle étape du processus, la fonction de rappel catch() est appelée pour gérer l'erreur.
```
> Il est important de noter que fetch() renvoie une Promesse (Promise), ce qui permet d'utiliser les méthodes <strong>then() et catch()</strong> pour gérer de manière asynchrone la réponse et les erreurs potentielles.

> La fonction fetch() offre de nombreuses possibilités de personnalisation, notamment l'ajout d'en-têtes HTTP, l'envoi de données dans le corps de la requête, la gestion des erreurs, etc. Elle est devenue l'une des méthodes les plus couramment utilisées pour effectuer des requêtes AJAX (Asynchronous JavaScript and XML) en JavaScript, raison pour laquelle sa comprehension est devenue indispensable.