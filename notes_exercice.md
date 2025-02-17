# Retour sur les concepts de l'excercice : exercice combiné

## OBJECTIFS DE L'EXERCICE
- Mettre en place la structure de mise en page CSS - Grid / Flex / Position
- Comprendre l'intérêt des variables CSS pour la gestion des couleurs
- Créer et personnaliser des boutons
- Intégrer des effets dynamiques avec les pseudo-classes
- Ajouter des transitions pour adoucir les changements d'état visuels
- Comprendre comment adapter dynamiquement la taille d'un élément en fonction de son contenu
- Ajouter des effets visuels
- Mise en place de techniques de contrôle qualité

## BREAKPOINTS
Les breakpoints sont utilisés pour rendre un site responsive en ajustant le layout en fonction de la taille de l'écran. Les breakpoints utilisés ici sont les suivants :
- `<992px`: Taille d'écran inférieure à 992px, généralement pour les mobiles ou petites tablettes.
- `>=992px`: Taille d'écran égale ou supérieure à 992px, souvent utilisée pour les tablettes en mode paysage et petits écrans d'ordinateur portable.
- `>=1200px`: Taille d'écran égale ou supérieure à 1200px, utilisée pour les grands écrans ou ordinateurs de bureau.
- `>=1400px`: Taille d'écran encore plus grande, idéale pour les très grands écrans.

L'utilisation de ces breakpoints permet de créer des layouts adaptatifs et d'ajuster les styles pour chaque taille d'écran.


## UTILISATION DE `@import` EN CSS 
`@import` permet de charger un fichier CSS à l'intérieur d'un autre fichier CSS. Cela permet de séparer le code en plusieurs fichiers et de mieux organiser le projet. 

**Avantages :**

- Une meilleure organisation du code CSS.
- La possibilité de gérer plus facilement des fichiers de styles séparés.

>Toutefois, il faut faire attention à son utilisation excessive car elle peut ralentir les performances en augmentant le nombre de requêtes HTTP.


## LES DOSSIERS CSS
Le dossier `CSS` est divisé en sous-dossier permettant une meilleure organisation des fichiers CSS nécesasires au développement du projet. 

- Dossier _base
- Dossier _composant
- Dossier _layout

### Dossier _base :
Le dossier `base` contient des règles génériques utilisées pendant le développement, telles que le reset CSS ou des styles de débogage. Il sert de base à l'ensemble du projet en réinitialisant les styles par défaut des navigateurs et en définissant des variables globales.

**Exemple de fichiers**
- dev.css
- variables.css
- reset.css

### Dossier _composant : 
Le dossier `_composant` contient des éléments individuels de l'interface selon la méthode de conception *Atomic Design*. Ce dossier peut inclure des *atomes* (éléments de base comme des boutons ou des champs de formulaire), des *molécules* (groupes d'atomes qui fonctionnent ensemble) et des *organismes* (groupes complexes d'atomes et de molécules).

**Exemple de fichiers**
- header.css
- nav-primairy.css
- fiche-produit.css
- boutons.css
- footer.css

### Dossier _layout : 
Le dossier `_layout` est responsable de la structure globale de la page, notamment des grilles et de la mise en page. Cela inclut la configuration des colonnes et des rangées pour organiser l'affichage des éléments.

**Exemple de fichiers**
- structure.css
- grille-primairy.css
- grille-menu.css
- grille-produits.css

>Vous retrouverez cette façon de faire plus détaillée dans des frameworks de développement comme Vue.js ou React. Ceci est une introduction plus adaptée à vos compétences techniques à ce qui sera vu plus tard. 


## LE FICHIER `reset.css`
Un `reset` CSS est une technique qui consiste à réinitialiser les styles par défaut des navigateurs pour éviter les incohérences entre différents navigateurs. Cela inclut des propriétés comme `margin: 0`, `padding: 0`, etc., pour uniformiser l'apparence d'un site web sur différents appareils.


## L'UTILISATION DE LA CLASSE `.interface`

La classe `.interface` est le conteneur principal du projet. Son rôle est de gérer la grille principale en utilisant CSS Grid. Elle détermine la disposition de l'ensemble du layout, avec une configuration par défaut d'une seule colonne, et passe à une configuration à deux colonnes pour les écrans plus grands grâce aux media queries.

## LA GRILLE PRINCIPALE DU PROJET

En mobile, la grille principale est sur une seule colonne (`grid-template-columns: 1fr`). 

Sur des écrans plus larges (`>=992px`), la grille devieest divisé en deux colonnes, où la première colonne prend 1 fraction (`1fr`) de l'espace et la seconde prend 2 fractions de l'espace (`2fr`). 

La deuxième colonne est subdivisée en deux rangées sur des écrans plus grands  (`grid-template-rows: 1fr 1fr;`).

## L'IMBRICATION DU CODE CSS

Les imbrications permettent d'appliquer des styles à des éléments enfants d'un élément donné. Par exemple, vous pouvez définir un style pour un `div` avec une classe particulière, puis cibler ses enfants en utilisant la syntaxe appropriée.

```css
nav ul{
    list-style: none;
    
    /* & est nécessaire devant un sélecteur d'attribut et ne réagit pas comme en SCSS. On l'utilise aussi pour les pseudo-éléments et les pseudo-classes &:hover par exemple. */
    & li{
        display: inline-block;
        margin-right: 1em;
    }

    /* En css vous devez avoir un sélecteur qui a un symbole, comme ici le fait d'utiliser une classe, le symbole du . est accepté, les autres & . > ~ [ */
    .uneClasse{

    }
}
```
## LES MÉDIAS QUERIES
### Imbrication des `media queries` 

Les media queries peuvent être imbriquées dans une règle CSS pour modifier le style en fonction des tailles d'écran. Par exemple, dans ce code, la règle `.interface` passe à une grille à 2 colonnes lorsque la largeur de l'écran est supérieure à 992px grâce à la media query `@media (min-width: 992px)`.

```css
.interface {
    display: grid;
    grid-template-columns: 1fr;
    height: 100vh;

    @media (min-width: 992px) {
        grid-template-columns: 1fr 2fr;
    }
}
```

### Pourquoi utiliser `min-width`

L'utilisation de `min-width` permet de définir des styles qui s'appliquent à partir d'une certaine largeur d'écran. Cela est particulièrement utile pour rendre un site web responsive en ajustant son layout à des écrans plus larges.


## UTILISATION DE `inherit`

La valeur `inherit` permet à un élément de prendre la valeur d'une propriété de son parent. Cela permet d'oublier un code hérité précédemment et de rétablir un comportement uniforme dans le code CSS.

## `margin: 0 auto` POUR CENTRER UN ÉLÉMENT

`margin: 0 auto` est une technique très courante pour centrer un élément horizontalement lorsque flex ou grid ne coopèrent pas. Cela fonctionne lorsque l'élément a une largeur définie.

## LE SÉLECTEUR `:nth-child(2)`

Le sélecteur `:nth-child(2)` cible le deuxième enfant d'un parent donné par exemple. Cette méthode permet de réduire l'utilisation de classes excessives, car elle vous permet de cibler un élément spécifique sans avoir à ajouter une classe supplémentaire.

Il faut faire attention de l'utiliser dans un groupe d'éléments permanents dans le projet. 

## DIVISION D'UN TEXTE AVEC `<span> </span>`
Diviser un paragraphe en plusieurs `<span> </span>` permet de cibler précisément certaines parties du texte pour les positionner librement sur la page, notamment avec le positionnement absolu. Comme `<span> </span>` est un élément en ligne, il n'interrompt pas le flux du texte, ce qui conserve l'organisation normale du paragraphe. Sur un écran desktop, cette méthode est idéale pour créer des mises en page créatives ou décalées, en profitant de l'espace disponible. De plus, avec des médias queries, on peut facilement revenir à une présentation classique sur des écrans plus petits, assurant une bonne lisibilité sur tous les appareils.


## LES IMAGES EN ARRIÈRE-PLAN

Les images d'arrière-plan sont définies avec la propriété `background-image`. Vous pouvez aussi contrôler leur affichage avec `background-position`, `background-repeat`, et `background-size`. 

Par exemple, dans ce code :
```css
background-image: url('../../assets/jpg/background-bouffe.jpg');
background-position: center;
background-repeat: no-repeat;
background-size: cover;
```
- background-size: cover : Assure que l'image couvre toute la zone, sans la déformer.
- background-position: center : Centrer l'image dans le conteneur.

Ce code permet de mieux manipuler les images surtout dans un contexte responsive où la taille de l'image doit s'adapter en fonction des nombreux breakpoints. 


## CRÉATION DES KITS DE BOUTONS
Des classes génériques de boutons sont créées, puis déclinées en différentes variantes. Cela permet de maintenir la cohérence et de réduire la duplication du code.

```css
.bouton{
    display: inline-flex;
    align-items: center;
    justify-content: center;
    width: auto; /* Empêche de prendre 100% */
    max-width: fit-content;
    padding: 0.5em 1em;
    font-size: 1rem;
    text-decoration: none;
    border: none;
    border-radius: 4px;
    background-color: #a0a0a0;
    color: #fff;
    cursor: pointer;
    transition: background-color 0.3s;

    &:hover{
        background-color: #333333;
    }
}

.boutton--medium{
    font-size: 1.2rem;
    padding: 0.75em 1.5em;
}

.bouton--primary {
    background-color: var(--noir);
    color: #fff;
    &:hover {
        background-color: var(--mauve);
    }
}
```
### Insertion d'effets de transition
Le transition permet de créer des effets fluides lorsque l'utilisateur interagit avec un élément.

```css
.bouton--primary {
    background-color: var(--noir);
    color: #fff;
    transition: background-color 0.3s; /* changement plus fluide */

    &:hover {
        background-color: var(--mauve);
    }
}
```

### Adaptation de la taille avec `max-width: fit-content`
La propriété max-width: fit-content permet à un élément de ne pas prendre plus d'espace que nécessaire, ce qui est utile pour des éléments comme des boutons qui doivent ajuster leur taille en fonction du contenu.

## EFFETS CSS `filter: drop-shadow`
La propriété filter: drop-shadow est utilisée pour ajouter une ombre portée à un élément. Cela est souvent utilisé pour donner un effet de profondeur aux éléments, comme les icônes.
```css
.social--link {
    filter: drop-shadow(3px 8px 6px rgba(0, 0, 0, 0.6));
}
```

## UTILISATION DES PSEUDO-ELEMENT `::before`
Utiliser le pseud-élément ::before permet d'ajouter du contenu avant un élément. Cela peut être utile pour ajouter une icône avant un lien, comme une icône de réseau social.

Avec la technique de l'imbrication, on peut facilement l'associé à un lien comme dans l'exemple suivant : 
```css
.social--link a{
    &::before{
        display: block;
        position: absolute;
        content: "";
        top: 0;
        right: -48px;
        width: 32px;
        height: 32px;
        background-image: url('../../assets/svg/icon-Facebook.svg');
        background-position: center;
        background-repeat: no-repeat;
        background-size: 24px 24px;
    }
}
```