# Vue.js - Évaluation

## Partie informatique

### Mise en place

1. Créer un nouveau projet intitulé `punk-ipa-project`, à l'aide de Vite (https://vitejs.dev/), en suivant la documentation : https://vitejs.dev/guide/ (choisir le template preset pour `vue`). Le projet doit avoir une structure très similaire à celle-ci :

   ```
   .
   ├── .gitignore
   ├── index.html
   ├── package.json
   ├── public
   │   └── favicon.ico
   ├── src
   │   ├── App.vue
   │   ├── assets
   │   │   └── logo.png
   │   ├── components
   │   │   └── HelloWorld.vue
   │   └── main.js
   └── vite.config.js
   ```

2. Installer toutes les dépendances.
3. Tester que tout fonctionne bien en lançant le serveur de développement puis en se rendant sur `localhost:3000`.
4. Installer `axios` (https://github.com/axios/axios).
5. Le design est toujours à ignorer, sauf lorsque demandé explicitement. Les bonnes pratiques sont à respecter : casse, indentation, orthographe, nommage des variables, nommage des fonctions, nommage des composants, etc.


### Initialisation

6. Supprimer le composant `HelloWorld.vue`.
7. Supprimer dans la vue `App.vue` toutes les références à `HelloWorld.vue`.
8. Modifier le logo de Vue.js par l'image suivante, au mêmes dimensions : https://www.beerwulf.com/globalassets/ipa-pack-nlfrbe-final-v3_pack_22681_0.png (si l'URL renvoie une erreur, utiliser une autre image de pUnk IPA au choix).
9. Appliquer les dimensions suivantes à l'image : 250px * 222px, en CSS, avec une classe CSS intitulée `logo-image`. Aide : https://v3.vuejs.org/guide/single-file-component.html. L'application doit alors répondre correctement dans le navigateur, en affichant simplement l'image d'appareil photo.

### Menu principal

10. Créer un nouveau composant `Title.vue` ayant en tant que `prop` une chaine de caractère obligatoire appelée `text`. Ce composant affiche le texte `text` dans un titre HTML de niveau 1, ayant la classe CSS `title`, comportant le CSS suivant :

```css
font-family: 'playball', cursive;
color: #fff;
margin: .2em .35em .18em .19em;
position: relative;
text-align: center;
padding: .4em 1em;
width: auto;
display: inline-block;
line-height: 1.5;
-webkit-transform: skew(0deg, -3deg);
-ms-transform: skew(0deg, -3deg);
transform: skew(0deg, -3deg);
transition: all .5s;
white-space: nowrap;

:before {
  z-index: -1;
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  height: 100%;
  width: 80%;
  background: #dd4f00;
  border-radius: 12px;
  -webkit-transform: skew(10deg);
  -ms-transform: skew(10deg);
  transform: skew(10deg);
}

:after {
  z-index: -1;
  content: '';
  position: absolute;
  top: 0;
  right: 0;
  height: 100%;
  width: 40%;
  background: #dd4f00;
  border-radius: 12px;
  -webkit-transform: skew(-20deg);
  -ms-transform: skew(-20deg);
  transform: skew(-20deg);
}
```

11. Créer 2 nouveaux composant dont l'élément racine est une `<section>` :

- `ListTab.vue`

- `DetailsTab.vue`

12. Ces 2 composants importent chacun le composant `Title.vue` , avec pour texte respectivement :

- Liste des bières

- Détail d'une bière

13. Ils importent aussi chacun le package `axios`.
14. Importer les deux composants précédents dans `App.vue`.
15. Créer un composant `Navbar.vue` à utiliser dans `App.vue`. Ce composant `Navbar.vue` comporte deux liens « Liste des bières » et « Détail d'une bière ». Implémenter dans ce composant un évènement personnalisé qui remonte au composant parent (`App.vue`) le lien qui a été cliqué. Implémenter dans `App.vue` un rendu conditionnel sur les deux composants `ListTab.vue` et  `DetailsTab.vue` pour afficher l'un ou l'autre en fonction du lien qui a été cliqué.

### Onglet liste

16. Dans le composant `ListTab.vue`, récupérer via l'API PunkAPI (https://punkapi.com) un tableau dans une variable de `data` comportant la liste de toutes les bières, sous cette forme :

```json
[
  {
    "id": 1,
    "name": "Buzz",
    "tagline": "A Real Bitter Experience.",
    "first_brewed": "09/2007",
    "description": "A light, crisp and bitter IPA brewed with English and American hops. A small batch brewed only once.",
    "image_url": "https://images.punkapi.com/v2/keg.png",
    "abv": 4.5,
    "ibu": 60,
    "target_fg": 1010,
    "target_og": 1044,
    "ebc": 20,
    "srm": 10,
    "ph": 4.4,
    "attenuation_level": 75,
    "volume": {
      "value": 20,
      "unit": "litres"
    },
    "boil_volume": {
      "value": 25,
      "unit": "litres"
    },
    "method": {
      "mash_temp": [
        {
          "temp": {
            "value": 64,
            "unit": "celsius"
          },
          "duration": 75
        }
      ],
      "fermentation": {
        "temp": {
          "value": 19,
          "unit": "celsius"
        }
      },
      "twist": null
    },
    "ingredients": {
      "malt": [
        {
          "name": "Maris Otter Extra Pale",
          "amount": {
            "value": 3.3,
            "unit": "kilograms"
          }
        },
        {
          "name": "Caramalt",
          "amount": {
            "value": 0.2,
            "unit": "kilograms"
          }
        },
        {
          "name": "Munich",
          "amount": {
            "value": 0.4,
            "unit": "kilograms"
          }
        }
      ],
      "hops": [
        {
          "name": "Fuggles",
          "amount": {
            "value": 25,
            "unit": "grams"
          },
          "add": "start",
          "attribute": "bitter"
        },
        {
          "name": "First Gold",
          "amount": {
            "value": 25,
            "unit": "grams"
          },
          "add": "start",
          "attribute": "bitter"
        },
        {
          "name": "Fuggles",
          "amount": {
            "value": 37.5,
            "unit": "grams"
          },
          "add": "middle",
          "attribute": "flavour"
        },
        {
          "name": "First Gold",
          "amount": {
            "value": 37.5,
            "unit": "grams"
          },
          "add": "middle",
          "attribute": "flavour"
        },
        {
          "name": "Cascade",
          "amount": {
            "value": 37.5,
            "unit": "grams"
          },
          "add": "end",
          "attribute": "flavour"
        }
      ],
      "yeast": "Wyeast 1056 - American Ale™"
    },
    "food_pairing": [
      "Spicy chicken tikka masala",
      "Grilled chicken quesadilla",
      "Caramel toffee cake"
    ],
    "brewers_tips": "The earthy and floral aromas from the hops can be overpowering. Drop a little Cascade in at the end of the boil to lift the profile with a bit of citrus.",
    "contributed_by": "Sam Mason <samjbmason>"
  },
  { ... },
  { ... },
  { ... },
  ...
]
```

​       S'aider de la documentation de l'API pour déterminer l'URL complète à appeler : https://punkapi.com/documentation/v2

17. Dans une computed du même composant, transformer le tableau récupéré via l'API (qui comporte un certain nombre d'objets avec beaucoup de propriétés) en tableau d'objets appelé `formattedBeerList` dont les propriétés sont seulement les suivantes :
    - `name` (nom de la bière),
    - `description` (description de la bière)
    - `abv` (poucentage d'alcool de la bière)

18. Afficher à l'aide de la directive appropriée tous les éléments de ce nouveau tableau sous forme de liste HTML.

### Onglet recherche classique

19. Dans le composant `DetailsTab.vue`, créer un formulaire simple comportant un champ nombre et un bouton de validation du formulaire intitulé « Rechercher ».

20. Lier le contenu du champ textuel à une variable de `data` nommée `beerId`.

21. Faire en sorte que la phrase suivante s'affiche lors du clic sur « Rechercher » si le contenu du champ est vide : « Veuillez renseigner un identifiant de bière. ».
22. Faire en sorte que la phrase suivante s'affiche lors du clic sur « Rechercher » si le contenu du champ n'est pas un nombre : « Veuillez renseigner un identifiant de bière valide. ».

23. Compléter le composant pour lancer la recherche lors du clic sur « Rechercher » et que le contenu du champ est correct. Pour cela, déterminer l'URL auprès de l'API (https://punkapi.com/documentation/v2), qui devra bien sûr comporter le contenu du champ.

24. Si le retour de l'API est en erreur ou que aucun résultat n'a été trouvée, i.e. si la bière semble ne pas exister, afficher la phrase : « La bière n'a pas été trouvée... ».

25. Si le retour de l'API est en succès (pour un identifiant de bière valide), récupérer dans une variable de `data` l'objet renvoyé, de la forme :

```json
{
  "id": 12,
  "name": "Arcade Nation",
  "tagline": "Seasonal Black IPA.",
  "first_brewed": "12/2015",
  "description": "Running the knife-edge between an India Pale Ale and a Stout, this particular style is one we truly love. Black IPAs are a great showcase for the skill of our brew team, balancing so many complex and twisting flavours in the same moment. The citrus, mango and pine from the hops – three of our all-time favourites – play off against the roasty dryness from the malt bill at each and every turn.",
  "image_url": "https://images.punkapi.com/v2/12.png",
  "abv": 5.3,
  "ibu": 60,
  "target_fg": 1012,
  "target_og": 1052,
  "ebc": 200,
  "srm": 100,
  "ph": 4.2,
  "attenuation_level": 77,
  "volume": {
    "value": 20,
    "unit": "litres"
  },
  "boil_volume": {
    "value": 25,
    "unit": "litres"
  },
  "method": {
    "mash_temp": [
      {
        "temp": {
          "value": 65,
          "unit": "celsius"
        },
        "duration": null
      }
    ],
    "fermentation": {
      "temp": {
        "value": 19,
        "unit": "celsius"
      }
    },
    "twist": null
  },
  "ingredients": {
    "malt": [
      {
        "name": "Pale Ale",
        "amount": {
          "value": 3.13,
          "unit": "kilograms"
        }
      },
      {
        "name": "Caramalt",
        "amount": {
          "value": 0.25,
          "unit": "kilograms"
        }
      },
      {
        "name": "Crystal 150",
        "amount": {
          "value": 0.18,
          "unit": "kilograms"
        }
      },
      {
        "name": "Carafa Special Malt Type 1",
        "amount": {
          "value": 0.25,
          "unit": "kilograms"
        }
      }
    ],
    "hops": [
      {
        "name": "Simcoe",
        "amount": {
          "value": 12.5,
          "unit": "grams"
        },
        "add": "start",
        "attribute": "bitter"
      },
      {
        "name": "Simcoe",
        "amount": {
          "value": 19,
          "unit": "grams"
        },
        "add": "middle",
        "attribute": "flavour"
      },
      {
        "name": "Simcoe",
        "amount": {
          "value": 12.5,
          "unit": "grams"
        },
        "add": "end",
        "attribute": "flavour"
      },
      {
        "name": "Amarillo",
        "amount": {
          "value": 12.5,
          "unit": "grams"
        },
        "add": "end",
        "attribute": "flavour"
      },
      {
        "name": "Citra",
        "amount": {
          "value": 12.5,
          "unit": "grams"
        },
        "add": "end",
        "attribute": "flavour"
      },
      {
        "name": "Simcoe",
        "amount": {
          "value": 62.5,
          "unit": "grams"
        },
        "add": "dry hop",
        "attribute": "aroma"
      },
      {
        "name": "Amarillo",
        "amount": {
          "value": 62.5,
          "unit": "grams"
        },
        "add": "dry hop",
        "attribute": "aroma"
      },
      {
        "name": "Citra",
        "amount": {
          "value": 62.5,
          "unit": "grams"
        },
        "add": "dry hop",
        "attribute": "aroma"
      }
    ],
    "yeast": "Wyeast 1056 - American Ale™"
  },
  "food_pairing": [
    "King prawn kebabs",
    "Halibut with a mango and tomato salad",
    "Mint chocloate ice cream"
  ],
  "brewers_tips": "Be as accurate as possible when weighing out your malts to ensure you strike the right balance.",
  "contributed_by": "Sam Mason <samjbmason>"
}
```

26. Afficher une image de la bière.

27. Afficher les informations suivantes :

- Le nom de la bière, dans un titre HTML de niveau 1
- Le pourcentage d'alcool, dans un champ HTML de haute importance (Aide : https://developer.mozilla.org/en-US/docs/Web/HTML/Element/strong)
- La date du premier brassage, dans un champ HTML `time` (Aide : https://developer.mozilla.org/en-US/docs/Web/HTML/Element/time)
- Le conseil du brasseur, dans un paragraphe HMTL

28. Afficher en plus des informations ci-dessus la liste de tous les ingrédients de la bière, sous forme de listes HTML imbriquées. Par exemple, pour l'exemple donné à l'étape 25, afficher :
```html
  <ul>
    <li>
      malt
      <ul>
        <li>Pale Ale</li>
        <li>Caramalt</li>
        <li>Crystal 150</li>
        <li>Carafa Special Malt Type 1</li>
      </ul>
    </li>
    <li>
      hops
      <ul>
        <li>Simcoe</li>
        <li>Simcoe</li>
        <li>Simcoe</li>
        <li>Amarillo</li>
        <li>Citra</li>
        <li>Simcoe</li>
        <li>Amarillo</li>
        <li>Citra</li>
      </ul>
    </li>
    <li>
      yeast
      <ul>
        <li>Wyeast 1056 - American Ale™</li>
      </ul>
    </li>
  </ul>
```

### Rendu

Zipper le projet `punk-ipa-project` pour créer le fichier `[nom]-[prenom].zip` (tout en minuscule, sans accent, au format ZIP et par RAR ni TAR ni GZIP ou autre). L'envoyer d'une part à l'adresse `timothe.crespy@lyon.ort.asso.fr`, et d'autre part à `Timothé Crespy` en message privé sur Microsoft Teams, avant 17h05.
