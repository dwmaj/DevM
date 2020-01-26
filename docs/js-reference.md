## JavaScript Quick Reference

### Accéder aux éléments du DOM

```javascript
// Obtenir une liste d'éléments grâce a un selecteur css
// Ici : tous les éléments ayant la class .someclass
// <li class="someclass">élément 1</li>
// <li class="someclass">élément 2</li>
// <li class="someclass">élément 3</li>
document.querySelectorAll('.someclass');

// Obtenir le premier élément qui correspond au sélecteur.
document.querySelector('.someclass');

// Le premier élément avec le data attribute correspondant. <div data-day="monday"></div>
const elements = document.querySelector('[data-day="monday"]');

// Obtenir une liste de tous les éléments correspondant au sélecteur.
document.querySelectorAll('div.note, div.alert');

// Obtenir une liste de tous les éléments avec le data attribute correspondant.
const elements = document.querySelectorAll('[data-day]');
```

### Add/Remove/Toggle/Check Classes

```javascript
// Selectionner l'élément dont on veut changer les 'classes'.
const el = document.querySelector('.my-element');

// Enlever la class 'bg-red'.
el.classList.remove('bg-red');

// Ajouter la class 'bg-blue'.
el.classList.add('bg-blue');

// Ajouter or enlever plusieurs classes
el.classList.add('foo', 'bar');
el.classList.remove('foo', 'bar');

// Si la class 'visible' est présente, l'enlever, sinon, l'ajouter.
el.classList.toggle('visible');

// Test si la classe est présente sur l'élément (retourne TRUE ou FALSE).
el.classList.contains('foo');
```

### Events

The Mozilla Developer Network has [a full list of available events](https://developer.mozilla.org/en-US/docs/Web/Events).

```javascript
const myLink = document.querySelector('.my-link');

function onClickFunc(e) {
    e.preventDefault(); // Eviter le comportement "normal" de l'événement
    const clickElement = e.currentTarget; // Récupérer l'élément cliqué
}

myLink.addEventListener('click', onClickFunc);
myLink.removeEventListener('click', onClickFunc);
```

### Attributes

```javascript
// Obtenir la valeur d'un attribut, par exemple le href d'un lien. <a href="page.html">Link</a>
const sandwich = elem.getAttribute('href');

// Obtenir la valeur d'un attribut, par exemple le href d'un lien. <div data-sandwich="club"></div>
const sandwich = elem.getAttribute('data-sandwich');

// Définir la valeur d'un attribut
elem.setAttribute('data-sandwich', 'fromage');

// Supprimer un attribut
elem.removeAttribute('data-sandwich');

// Vérifier si un élément a un attribut
if (elem.hasAttribute('data-sandwich')) {
    // do something...
}
```

### Boucle

```javascript
// Boucler dans une liste d'élément
const list = document.querySelectorAll('.item');

list.forEach((element) => {
    console.log(element);
});
```

### window.location

```javascript
// Récupérer l'url entière de la page en cours.
const url = window.location.href;

// Charger une autre page
window.location.href = "http://www.google.be";

// Récupérer la partie de l'URL qui suit le symbole « # », s'il y en un, avec ce symbole inclus. 
const hash = window.location.hash;
console.log(hash);
// Si url dans la barre du navigateur est http://www.example.com/home/#test
// Console output : #test
```

### String slice

```javascript
const text = 'Bonjour je suis une phrase';

// Extraire une partie du texte : après le 8ème caractère jusqu'à la fin
const startAtHeight = text.slice(8);
console.log(startAtHeight);
// Console output : "je suis une phrase"

// Extraire une partie du texte : après le 8ème caractère et s'arrêter au 15ème.
const startAndEnd = text.slice(8, 7);
console.log(startAndEnd);
// Console output : "je suis"

// Extraire une partie du texte : du début et s'arrêter au 7ème caractère en commancant par la fin.
const sliceFromTheEnd = text.slice(0, -7);
console.log(sliceFromTheEnd);
// Console output : "Bonjour je suis une"
```

### Créer des nouveaux éléments

```javascript
// Créer des éléments
const newHeading = document.createElement('h1');
const newParagraph = document.createElement('p');

// Ajouter du texte dans un élément
newHeading.innerHTML = 'This is a nice <span>header</span> text!';

// On peut maintenant les ajouter dans le DOM (voir section "Ajouter des éléments dans le DOM")
```

### Ajouter des éléments dans le DOM

```javascript
// Sélectionner l'élément dans lequel on veut ajouter d'autres éléments.
const myDiv = document.querySelector('.my-div');

// ajouter les éléments précédemment créé.
myDiv.appendChild(newHeading);
myDiv.appendChild(newParagraph);

// Supprimer un éléments à l'intérieur de son parent
myDiv.removeChild(newParagraph);
```

### Objects notation

La "dot notation" (`obj.something`) ou "bracket notation" (`obj['something']`) permet d'ajouteur des paires "clé/valeur" à un object

```javascript
// Créer un objet.
const lunch = {
    sandwich: 'poulet',
    drink: 'soda'
};

// Changer un élément en utilisant la notation 'dot'
lunch.drink = 'water';

// Ajouter un élément en utilisant la notation '[]'
lunch["dessert"] = 'cookies';
```

### Fetch

```javascript
// Charger le contenu du fichier 'file.txt', récuperer le texte et l'afficher dans un élément
fetch('/data/file.txt')
.then(function(response) {
    return response.text();
})
.then(function(text) {
    const el = document.querySelector('.my-element');
    el.innerHTML = text;
});

// Charger le contenu du fichier 'file.json', 'parser' le json et l'afficher dans la console
fetch('/data/file.json')
.then(function(response) {
    return response.json();
})
.then(function(data) {
    console.log(data);
});
```

### JSON File

```javascript
[{
  "id": 1,
  "first_name": "Jeanette",
  "last_name": "Penddreth",
  "email": "jpenddreth0@census.gov",
  "gender": "Female",
  "ip_address": "26.58.193.2"
}, {
  "id": 2,
  "first_name": "Giavani",
  "last_name": "Frediani",
  "email": "gfrediani1@senate.gov",
  "gender": "Male",
  "ip_address": "229.179.4.212"
}, {
  "id": 3,
  "first_name": "Noell",
  "last_name": "Bea",
  "email": "nbea2@imageshack.us",
  "gender": "Female",
  "ip_address": "180.66.162.255"
}, {
  "id": 4,
  "first_name": "Willard",
  "last_name": "Valek",
  "email": "wvalek3@vk.com",
  "gender": "Male",
  "ip_address": "67.76.188.26"
}]
```

### JSON Parsing

```javascript
const lunch = {
    sandwich: 'poulet',
    drink: 'soda'
};

// Encoder l'object en 'json'
const json = JSON.stringify(lunch);
console.log(json);
// Console output: "{"sandwich":"poulet","drink":"soda"}"

// Décoder un 'json' en object
const json = '{"result":true, "count":42}';
obj = JSON.parse(json);

console.log(obj.count);
// Console output: 42

console.log(obj.result);
// Console output: true
```

### Array Push

```javascript
// Ajouter un élément à un tableau
const sandwich_item = ['poulet', 'fromage'];
sandwich_item.push('mayo');
```

### LocalStorage

```javascript
// Ecrire une clé/valeur dans le 'local storage'.
window.localStorage.setItem('city', 'Paris');

// Récupérer une clé/valeur depuis le 'local storage'.
const city = window.localStorage.getItem('city');
```

### Form Field Value

```html
<form class="js-form">
    <input type="text" name="name" value="">
    <input type="email" name="email" value="">
    <button type="submit">Send</button>
</form>
```

```javascript
const form = document.querySelector('.js-form');
form.addEventListener('submit', function(e) {
  e.preventDefault();
  // On récupère les champs du formulaire
  const inputs = form.elements;
  // On utilise ce tableau pour récupérer la valeur du champ email
  const email = inputs['email'].value
  console.log(email)
});
```

