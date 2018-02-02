# Documentation

## Les @font-face

Utiliser les @font-face dans le css permet de définir en local les polices à utiliser pour les afficher dans la page web.

Propriété font-family et src :

```css
@font-face {
  font-family: 'Raleway_bold';
  src: url(font/Raleway_bold.ttf);
  /*J'ai nommé la police Raleway_bold et je vais la chercher dans mon dossier font*/
}
```

Appel de la @font-family : 

```css
.text {
  font-family: 'Raleway_bold';
  font-size: 22px;
  color: #fff;
}
```

* @font-face supporté par IE, Opera, Chrome, Safari . 
* formats .ttf .otf .woff supportés par les 5 navigateurs = à privilégier .

## Media queries



## Convention BEM
* B -> Block
* E -> Element
* M -> Modifier

```html
<!-- mainList = Block -->
<ul class="mainList mainList--xmas" >
  <!-- __item = Element -->
  <li class="mainList__item">
    <!-- __itemLink = Element -->
    <a href="/home" class="mainList__itemLink mainLink--isActive">Home</a>
  </li>

  <li class="mainList__item">
    <!-- __itemLink = Element -->
    <a href="/about" class="mainList__itemLink">About</a>
  </li>

  <li class="mainList__item">
    <!-- __itemLink = Element -->
    <a href="/works" class="mainList__itemLink">Works</a>
  </li>

</ul>
```
```css
.mainList{
    display:flex;
    justify-content space between.
    &--xmas{background:green}
    &__item{
      list-style:none
    }
    &__itemLink{
      color: red;
      &--isActive {
        color: white;
      }
    }  
  }
```

Exemple en CSS du rendu :

```css
.mainList{

}
.mainList--xmas{

}
.mainList__item{

}
.mainList__itemLink{

}
.mainList__itemLink--isActive {

}
```

## Pseudo attributs

Les pseudo attributs `before`et `after` permettent de créer des noeuds HTML en CSS.
Ils sont essentiellement utilisés pour ajouter des ornements, des décorations ... On peut bien entendre faire des animations avec, les positionner par rapport à leur parent (relative/ absolute). **Ils doivent obligatoirement avoir un `content :''`** afin de s'afficher.

```html
<section class="cover">
  <h1 class="cover__mainTitle">
    Présentation des pseudo-attributs
  </h1>
</section>
```

```css
.cover{
  background: #FDFDFD;
  padding: 20px;
  &__mainTitle{
    text-align: center;
    font-size: 24px;
    color: green;
    position: relative;

    &::before,
    &::after{
      content:' Hello';
        color: white;
      display: block;
      width: 50px;
      height: 50px;
      background: green;
      top: 0;
      position: absolute;

    }
    &::before{left: 0;
    }
    &::after{right: 0
    }
  }
}
```


## REM, EM, %, VW Sizing

### %

### EM

* Relative à ma taille de son parent.

```css
.cover{
  font-size: 100%;
  /* 100% = 16px */
  &__mainTittle{
    /* 1em = 16px / .em =/= 16px */
    font-size: .8em;
  }
}
```

### REM

* Le REM est basé sur la taille de la racine (soit la balise <html>) qui, par défaut a une valeur de 16px. Afin d'éviter tout calcul, il est nécesssaire de l'écraser en donnant une base de 10px soit 62.5%.
* Le REM est intéressant à utiliser si les media-queries employées sont en rem également. Cela vous permettra de garder des proportions égales lorsqu'on va redimensionner la page.
* Ses proportions seront également gardées quand l'utilisateur zoomera dans votre page.

```css
html{
  font-size: 62.5%;
}
.mainTitle{
  /* 1.6 rem == 16px*/
  font-size: 1.6rem;
  /* */
  width: 32rem;

}
```

### VW(width)/ VH(height)

* Unités relatives à la taille de votre écran (peur importe le device)
* Attention au VH et à son contenu. 100vh == 100vh quoi qu'il arrive.
* VW : très utile pour les interfances fluides.

## FlexboxGrid

Les modificateurs responsives permettent de spécifier différentes tailles de colonnes, décalages, alignement et distribution aux largeurs de la fenêtre xs (= smartphone), sm (= smartphone large), md (= tablette) & lg (= desktop).

* on peut imbriquer des grids dans des grids
* les flexboxgrids fonctionnent en flex, on peut donc leur appliquer toutes les propriétés des flexbox grâce aux classes prédéfinies
* NE JAMAIS UTILISER DE MARGIN / PADDING SUR LES BLOCS AUXQUELS SONT APPLIQUÉS LES CLASSES XS, SM, MD ET LG ( => CASSE LA GRILLE)

```html
<div class="container-fluid">
    <!-- toujours créer un container qui va contenir la grille -->
    <!-- la classe fluid evite le changement brutal de la page au breakpoint de la media query -->
    <div class="row between-xs">
      <!-- classe between-xs = en flexbox (justify-content: space-between) -->
      <div class="col-xs-6 col-sm-4">
        <h2>lorem</h2>
        <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute
          irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>
      </div>
      <div class="col-xs-6 col-sm-4">
        <h2>lorem</h2>
        <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute
          irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>
      </div>
      <div class="col-xs-6 col-sm-4">
        <h2>lorem</h2>
        <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute
          irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>
      </div>
      <div class="col-xs-offset-1 col-xs-5 col-sm-4">
        <!-- offset permet de décaler le bloc vers la droite du nombre de colonnes voulu. Ici, sur ecran smartphone on décale le bloc d'une colonne -->
        <h2>lorem</h2>
        <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute
          irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>
      </div>
      <div class="col-xs-12 col-sm-4">
        <h2>lorem</h2>
        <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute
          irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>
      </div>
    </div>
  </div>
```


## Liens utiles :
* [Caniuse](http://caniuse.com) : c'est compatible ou pas .
* [Flexboxgrid] (http://flexboxgrid.com/) : travailler avec les grilles directement dans le html .
* (https://davidwalsh.name/write-media-queries-sass) : media-queries avec sass .
