SER - Laboratoire 1
===================

_Sacha Bron, Léonard Berney_

Introduction
------------

Le but de ce laboratoire est de préparer des structures de données afin de les utiliser lors du développement de l'application que nous allons effectuer durant les prochains labos.

Commentaires
------------

Durant la création des différents fichiers, nous avons dû faire certains choix. Cette section les présente.

### XML

Le XML est séparé en 5 parties:
- les _films_
- les _acteurs_
- les _genres_
- les _langues_
- les _salles_

De plus, les _films_ contiennent 4 sous-parties:
- les _roles_
- les _projections_
- les _mots-clés_
- les _critiques_

### DTD

Un _film_ peut ne pas avoir d'acteur qui joue dedans. C'est pourquoi _roles_ est optionel.
Un _film_ peut ne jamais être projeté. C'est pourquoi _projections_ est optionel.
Un _film_ peut ne pas avoir de critique. C'est pourquoi _critiques_ est optionel.

_Genres_, _langues_ et _salles_ sont des structures de données externes à _films_, ce qui nous permet de les référencer et d'éviter des duplications de données. Par exemple, si un genre est ajouté, ou une salle est supprimée, il n'est pas nécessaire de modifier le contenu de _genresFilm_, _langueFilm_ ou _salleProjection_.  
De même, les _role_ contiennent un attribut `acteur` qui fait référence à un _acteur_.

Comme nous ne pouvons pas insérer directement des données binaires dans le XML, l'_image_ du film contient uniquement un attribut `src` contenant un lien vers l'image du film. Le chemin vers cette image peut être absolu ou relatif au document XML.

### Json

Le document Json est relativement simple. Il contient un tableau de toutes les projections, et chaque projection contient directement les données nécessaires.


Conclusion
----------

Nous pouvons remarquer que le XML, contrairement au Json, doit être formater selon un squelette bien précis: le DTD. De cette façon, le programme développé lisant les fichiers XML sera plus fiable. En effet, il lui suffit de pouvoir parser tous documents respectant le XML pour être sûr de ne pas planter.

À l'inverse, un programme lisant des Json doit vérifier que chaque clé existe bel et bien dans l'arbre.
