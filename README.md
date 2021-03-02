# WKSHP-VueJS_to_do_list

![To do List preview](https://github.com/FlorenceJacobs/to_do_list_vueJS/blob/main/capture_to_do_list_vueJS.png?raw=true)

## Installer le projet
1. Cloner le repo en localhost (Wamp/Xamp/Lamp) :point_right: `git clone`
https://github.com/FlorenceJacobs/WKSHP-VueJS_to_do_list.git

2. Se rendre dans le dossier du projet
:point_right: `cd WKSHP-VueJS_to_do_list.git`

3. Lancer le projet dans votre IDE
:point_right: `code .`

4. Installer le projet
:point_right: `npm install`<br>
Puisque Bootstrap est dans le package.json, il s’installe automatiquement au moment du "npm install"<br>
:point_right: `npm run serve`<br>
Vous obtenez un message comme celui-ci :
> App running at:
>  - Local:   http://localhost:8080/<br>

Vous pouvez vous rendre sur votre localhost. Vous obtenez une page blanche, c’est normal.

## Exercice en sous-groupes

* **Groupe 1** :
* **Groupe 2** :
* **Groupe 3** :
* **Groupe 4** :

En sous-groupes, vous allez réaliser une to-do liste en suivant ces indications :

### 1. Créer l'input dans le composant parent **`App.vue`** 
Créer l’input pour introduire un nouvel item à la liste (et profitez-en pour ajouter un titre ou deux)<br>
Sous les “tags” qui appellent le composant enfant `<headerList>`, créez à l’aide de boostrap :

- `container`
  - `row`
  - `col`
     - `h1`
     - `h2`
     - `form class="form-group`
        - `label for="list"`
        - `input type="text" class="form-control" id="list" placeholder="Type something to do"`
        - `button class="btn”`

Feel free de customiser avec les classes bootstrap.<br>
C’est beau? On continue :

## 2. Récupérer le contenu de l'input

A présent, on va faire en sorte que l’élément que vous tapez dans l’input s’ajoute à une array au moment du “click” sur le button.

:one: **Capter le contenu inséré dans l’input**
`v-model = “element”`<br>
et déclarer la variable `element` dans script<br>
```
data() {
    return {
        listElement : [],
        element : "",
     }
},
```
   
:two: **Lancer une méthode au click sur le bouton**
`v-on:click(ou @click).prevent = “doThat”`<br>
REM : le `.prevent` empêche la page de se recharger au click<br>
Et dans `<script>` :
```
methods: {
    doThat: function() {
    ...........;
    }
}
```
  
:three: **On vérifie que ça fonctionne**<br>
Insérez l’array `listElement` dans le `<template>` sous la forme `{{ listElement }}`.<br>
Essayer d’ajouter des éléments à votre To do list. Ça marche? Alors on efface le `{{ listElement }}` et on passe à la suite.<br>


## 3. Afficher la liste dans un nouveau composant
À présent, il faudrait que les éléments de votre liste `{{ listElement }}` s’affichent dans un nouveau composant enfant:
  - :one: Créer le composant enfant `List.vue` et lui donner un nom d’exportation dans `export default`
  - :two: Importer le composant enfant dans le composant parent et lui donner le nom que l’on souhaite utiliser comme *tag* dans <br>
 ```
 components: {
      'headerList' : HeaderList,
       .... : ....,
},
```

  - :three: Faire passer des données (l’array `listElement`) du composant parent au composant enfant. Pour cela, utiliser les “props”:
      - a. Dans le *tag* (dans le composant parent), utiliser `v-bind:listElement="listElement"`
      - b. Dans le composant enfant, utiliser `props: ['listElement']`
  - :four: Faire apparaître chaque élément de l'array dans une `<li>` en bouclant sur `listElement` grâce à `v-for` (attention, pour que ça fonctionne, il faut coupler avec `v-bind:key="index"`).
  - :five: Ajouter un bouton pour supprimer un élément de la liste :
      - a. Dans la boucle, ajouter un `<button>` et y associer une méthode grâce à `v-on:click(ou @click)="doThat(onThis)"`
      - b. Déclarer la méthode (supprimer l’élément[x] de l’array `listElement` au click sur le bouton :
```
methods: {
    doThat: function(onThis) {
    .........;
    }
}
```

- :six: Enfin, le composant enfant qui contient les éléments de la liste s’affiche par défaut, même lorsqu'il est vide. Il faudrait ajouter une condition au *tag* qui appelle le composant enfant uniquement s’il contient au moins un élément dans la liste. Si la liste est vide, le composant enfant ne s’affiche pas.

`v-if=........`

Et voilà, s’il vous reste du temps, vous pouvez mettre en forme !
