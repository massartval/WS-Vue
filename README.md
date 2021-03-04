# WORKSHOP-VueJS. To do list.

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

* **Groupe 1** : Yvan, Abderrahman, Julien
* **Groupe 2** : Yannick, Antoine, Manon
* **Groupe 3** : Olivia, Nathanaël, Pauline
* **Groupe 4** : Gaetano, Valentin, Frédéric
* **Groupe 5** : Dorian, Thomas, Jonathan, Philippe

En sous-groupes, vous allez réaliser une to-do liste en suivant ces indications :

### 1. Créer l'input dans le composant parent **`App.vue`** 
Dans `App.vue`, vous aller créer un titre, un sous-titre, et l’input pour introduire un nouvel item à la liste<br>
Vous créez ces éléments à l’aide de boostrap sous les “tags” `<headerList>` qui appellent le composant enfant:

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
C’est beau ? On continue :

## 2. Récupérer le contenu de l'input

Au “click” sur le button, le contenu de l’input s’ajoute à une array .

:one: **Capter le contenu inséré dans l’input**<br>
A/ Capter le contenu de l'input. Indice : `v-model = "element"`<br>
B/ Déclarer la variable utilisée dans v-model (`"element"` dans l'exemple) dans `data`<br>
```
data() {
    return {
        listElement : [],
        element : "",
     }
},
```
   
:two: **Appeler une méthode au click sur le bouton**<br>
A/ Appeler la méthode dans le bouton. Indice : `v-on:click(ou @click).prevent = “doThat”`<br>
*REM : le `.prevent` empêche la page de se recharger au click*<br>
B/ Déclarer cette méthode de votre choix dans `<script>` :
```
methods: {
    doThat: function() {
    ...........;
    }
}
```
  
:three: **Vérifier que ça fonctionne**<br>
Insérez l’array `listElement` dans le `<template>` sous la forme `{{ listElement }}`.<br>
Essayer d’ajouter des éléments à votre To do list. Ça marche? Alors on efface le `{{ listElement }}` et on passe à la suite.<br>


## 3. Afficher la liste dans un nouveau composant
À présent, il faudrait que les éléments de votre array `{{ listElement }}` s’affichent dans un nouveau composant enfant:
  - :one: Créer le composant enfant `List.vue` et lui donner un nom d’exportation dans `export default`
  - :two: Importer le composant enfant dans le composant parent et lui donner le nom que l’on souhaite utiliser comme *tag* dans <br>
 ```
 components: {
      'headerList' : HeaderList,
       .... : ....,
},
```

  - :three: Faire passer des données du composant parent au composant enfant. Dans notre cas, la donnée à faire passer est l’array `listElement`. Pour cela, utiliser les “props”:
      - a. Dans le composant parent, ajouter au *tag* qui appelle le composant enfant `v-bind:listElement="listElement"`.
      - b. Dans le composant enfant, utiliser `props: ['listElement']`.
  - :four: Faire apparaître chaque élément de l'array `listElement` dans une `<li>` grâce à la boucle `v-for` (attention, pour que ça fonctionne, il faut coupler avec `v-bind:key="index"`).
  - :five: Ajouter un bouton pour supprimer un élément de la liste :
      - a. Dans la boucle, ajouter un `<button>` et y appeler une méthode au clic. Indice : `v-on:click(ou @click)="doThat(onThis)"`
      - b. Déclarer cette méthode qui permet de supprimer l’élément[x] de l’array `listElement` au click :
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
