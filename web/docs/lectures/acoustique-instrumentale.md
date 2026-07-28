# Acoustique instrumentale

<!--
## Objectifs

- distinguer excitateur, vibrateur, résonateur et rayonnement ;
- comprendre les modes de vibration d’une corde, d’une membrane et d’une
  colonne d’air ;
- relier mode de jeu et contenu spectral ;
- comparer les grandes familles d’instruments sans entrer dans une modélisation
  mathématique détaillée.
-->
  
## Un modèle général de l’instrument

Un instrument acoustique associe généralement plusieurs fonctions :

1. un apport d’énergie par le musicien ;
2. un **excitateur** : doigt, archet, marteau, anche, jet d’air ;
3. un **élément vibrant** : corde, membrane, plaque ou colonne d’air ;
4. un **résonateur** qui renforce et colore certaines fréquences ;
5. un mécanisme de **rayonnement** qui transmet le son à l’air.

Ces fonctions peuvent être réunies dans un même objet ou réparties entre
plusieurs éléments. Dans une guitare, par exemple, la corde vibre mais rayonne
peu directement : elle transmet son mouvement à la table d’harmonie.

## Cordes vibrantes

Les vibrations d’une corde sont principalement transversales. Une corde fixée
à ses deux extrémités possède plusieurs modes de vibration.

<figure>
<img src="../../res/cordemasses.gif" class="mx-auto d-block" width="60%">
</figure>

<video width="100%" controls="controls">
  <source src="../../res/corde234.mp4" type="video/mp4">
</video>

La fréquence fondamentale dépend :

- de la longueur \(L\) de la corde ;
- de sa tension \(T\) ;
- de sa masse par unité de longueur \(M\).

$$
f_1 = \frac{1}{2L}\sqrt{\frac{T}{M}}
$$

Il n’est pas nécessaire de mémoriser la formule. Elle indique simplement que :

- raccourcir la corde rend le son plus aigu ;
- augmenter sa tension rend le son plus aigu ;
- utiliser une corde plus lourde rend le son plus grave.

Les fréquences des modes sont des multiples de la fondamentale :

$$
f_n = n f_1
$$

### Influence du point d’excitation

Le mouvement de la corde est une combinaison de plusieurs modes. Leur amplitude
dépend du point et du type d’excitation.

Une corde pincée en son centre ne peut pas exciter efficacement les modes qui
ont un nœud à cet endroit : les harmoniques pairs sont fortement réduits. Une
corde pincée près d’une extrémité excite davantage les harmoniques élevés et
produit un son plus brillant.

<figure>
<img src="../../res/cordespincees.gif" class="mx-auto d-block" width="80%">
<figcaption><center><i>Spectres d’une corde pincée en son centre et au cinquième de sa longueur.</i></center></figcaption>
</figure>

Le matériau du plectre, la dureté d’un marteau ou la position d’un archet
modifient également le spectre et les transitoires.

## Membranes, plaques et barres

Une corde est un système vibrant à une dimension. Les membranes et les plaques
vibrent selon deux dimensions et présentent des modes plus complexes.

On rencontre notamment :

- des membranes dans les tambours ;
- des plaques dans les cymbales et les gongs ;
- des barres dans les xylophones et vibraphones ;
- des « coques » vibrantes dans les cloches ;
- des plaques dans les tables et caisses d’instruments à cordes.

<figure>
<img src="../../res/chladmi.gif" class="mx-auto d-block" width="80%">
<figcaption><center><i>Principaux modes d’une membrane circulaire idéale.</i></center></figcaption>
</figure>

Les figures ci-dessus rendent visibles les lignes qui restent presque
immobiles. Du sable posé sur une plaque vibrante s’y accumule :

<center>
<iframe width="560" height="315" src="https://www.youtube.com/embed/wvJAgrUBF4w?si=KJ9qNyAU6ZbawOn3" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</center>

Les fréquences de ces modes ne forment généralement pas une série harmonique
simple. C’est pourquoi les cloches, gongs et cymbales produisent souvent des
sons inharmoniques.

## Colonnes d’air et instruments à vent

Dans un instrument à vent, l’élément résonant principal est une colonne d’air.
L’excitation peut être produite par :

- un jet d’air sur un biseau, comme dans une flûte ;
- une anche simple, comme dans une clarinette ;
- une anche double, comme dans un hautbois ;
- les lèvres du musicien, comme dans une trompette.

### Tuyau ouvert

Un tuyau idéal ouvert aux deux extrémités possède une fondamentale :

$$
f_1 = \frac{c}{2L}
$$

Sa série de résonances contient tous les multiples de la fondamentale.

### Tuyau fermé

Un tuyau idéal fermé à une extrémité possède une fondamentale approximativement
une octave plus grave qu’un tuyau ouvert de même longueur :

$$
f_1 = \frac{c}{4L}
$$

Dans le modèle idéal, seules les résonances de rang impair sont présentes.

<figure>
<img src="../../res/tuyaux.gif" class="mx-auto d-block" width="60%">
</figure>

<figure>
<img src="../../res/tubecylindric.gif" class="mx-auto d-block" width="80%">
</figure>

La clarinette se rapproche, dans son registre grave, d’un tuyau cylindrique
fermé à une extrémité, ce qui contribue à l’importance de ses harmoniques
impairs. La flûte se rapproche d’un tuyau ouvert. Un conduit conique, comme
celui du hautbois ou du saxophone, présente une série de résonances plus proche
de celle d’un tuyau ouvert.

Les instruments acoustiques s’écartent de ces modèles : pavillon, trous, embouchure,
pertes, doigtés et intensité de jeu déplacent les résonances et modifient le
rayonnement.

## Couplage entre excitateur et résonateur

Le musicien n’impose pas toujours directement la fréquence. Dans les
instruments auto-entretenus — voix, vents, cordes frottées — l’excitateur et le
résonateur s’influencent mutuellement.

Par exemple :

- l’anche d’une clarinette est entraînée par le souffle, mais la colonne d’air
  sélectionne les régimes stables ;
- l’archet fournit continuellement de l’énergie à la corde ;
- les lèvres d’un trompettiste s’accordent sur une résonance du tube.

Cette interaction explique la richesse, mais aussi les difficultés de contrôle,
de nombreux instruments.

<!--
## Activités

1. Comparer une corde pincée près du centre et près du chevalet.
2. Associer plusieurs instruments à un modèle : corde, membrane, plaque, barre
   ou colonne d’air.
3. Identifier l’excitateur, le vibrateur et le résonateur de cinq instruments.
4. Comparer à l’oreille les attaques d’une même note jouée *sul tasto* et
   *sul ponticello*.
-->

## À retenir

- Un instrument associe excitation, vibration, résonance et rayonnement.
- Longueur, tension et masse déterminent la hauteur d’une corde.
- Le point d’excitation modifie le contenu harmonique.
- Membranes et plaques produisent souvent des partiels inharmoniques.
- Les modèles de tuyaux ouverts et fermés expliquent une partie du
  fonctionnement des vents, mais les instruments réels sont plus complexes.

## Aller plus loin

Si l'acoustique instrumentale vous intéresse, nous vous recommandons
« The Physics of Musical Instruments » de Thomas D. ROSSING.
