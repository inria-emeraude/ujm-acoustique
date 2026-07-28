# Psychoacoustique : du signal à la perception

<!--
## Objectifs

- distinguer une grandeur physique de la sensation associée ;
- expliquer simplement la hauteur virtuelle, la sonie et le masquage ;
- comprendre quelques mécanismes de reconnaissance et d’organisation des sons ;
- connaître les principaux indices de localisation.
-->

## Qu’étudie la psychoacoustique ?

La psychoacoustique étudie les relations entre les caractéristiques physiques
d’un son et la manière dont ils sont perçus par l'oreille humaine. Ces deux 
aspects ne coïncident pas toujours :

- deux sons physiquement différents peuvent être perçus comme semblables ;
- une même différence physique peut être très audible dans un contexte et
  presque imperceptible dans un autre ;
- le cerveau complète et organise les informations reçues.

## Sensibilité de l’oreille

Le domaine audible humain s’étend approximativement de 20 Hz à 20 kHz, mais
l’oreille n’est pas également sensible à toutes les fréquences. Elle est
particulièrement sensible aux fréquences moyennes, notamment dans la région
occupée par la voix.

À faible niveau, les graves et les aigus paraissent moins présents. Lorsque le
niveau augmente, l’équilibre perçu entre les régions du spectre se modifie.

Ce concept est présenté plus en détail [ici](propagation-reception.md#la-reception-du-son).

### La fondamentale absente

Un son contenant des partiels à 400, 600, 800 et 1 000 Hz peut produire une
hauteur fondamentale de 200 Hz, même si 200 Hz n’est pas physiquement présent.
Le système auditif utilise l’espacement régulier des harmoniques pour
reconstituer cette hauteur.

Ce concept est présenté plus en détail [ici](parametres-du-son.md#hauteur-percue).

## Niveau et sonie

Le niveau en décibels décrit le signal physique. La **sonie** correspond à la
sensation de force sonore.

Elle dépend notamment :

- du niveau ;
- de la fréquence ;
- de la durée ;
- de la présence d’autres sons ;
- de l’auditeur.

Une augmentation de 10 dB est souvent perçue approximativement comme un
doublement de la sonie, mais il ne s’agit pas d’une loi absolue.

Ce concept est présenté plus en détail [ici](parametres-du-son.md#amplitude-et-niveau-sonore).

## Le masquage

Un son peut rendre un autre son difficile ou impossible à entendre. Ce
phénomène est appelé **masquage**. Il est important lorsque les sons :

- ont des fréquences proches ;
- se produisent au même moment ;
- ont des niveaux très différents.

Le masquage joue un rôle dans l’orchestration, le mixage, l’intelligibilité de
la voix et la compression audio. Un instrument peut être présent dans le signal
mais devenir inaudible parce qu’un autre occupe la même région spectrale avec
un niveau supérieur.

Le programme Faust suivant illustre ce phénomène en masquant progressivement
le son d'une sinusoïde avec du bruit blanc :

<p>
<faust-editor>
<!--
import("stdfaust.lib");
noiseGain = hslider("Noise Level (dB)", -90,-90,0,0.01) : ba.db2linear;
process = (os.osc(440)/100 + no.noise*noiseGain)/2
    <: _,_; // stereo
-->
</faust-editor>
</p>

L'effet de masquage est notamment exploité dans la compression audio (ex. mp3).
Si un son au volume élevé est immédiatement suivi d'un son au volume beaucoup
plus faible, ce dernier ne sera peut-être pas entendu. Il est alors possible de
supprimer ce son pour gagner quelques échantillons d'enregistrement. 

## Timbre et reconnaissance

Le timbre dépend du spectre, mais aussi de l’évolution temporelle. L’attaque
d’un son fournit des indices très importants sur le geste et la source.

Si l’on retire l’attaque d’un son de piano, de guitare ou de percussion,
l’instrument devient souvent plus difficile à reconnaître. À l’inverse, une
attaque caractéristique suivie d’un son simplifié peut suffire à évoquer un
instrument.

Arrivez-vous à reconnaître le son de cet instrument ? :

<audio controls=""><source src="../../res/fadePiano.wav"></audio>

Il s'agit d'un de piano dont l'attaque a été supprimée. Voilà le son 
original :

<audio controls=""><source src="../../res/piano.wav"></audio>

## Regrouper et séparer les sons

Le système auditif organise en permanence la scène sonore. Des composantes ont
tendance à être regroupées lorsqu’elles :

- commencent et s’arrêtent ensemble ;
- évoluent de manière semblable ;
- sont harmoniques entre elles ;
- proviennent de la même direction.

Des différences de hauteur, timbre, rythme ou position permettent au contraire
de séparer plusieurs lignes musicales. Ces mécanismes interviennent dans
l’écoute d’une polyphonie, d’un orchestre ou d’un mixage.

Le programme Faust suivant implémente 3 oscillateurs sinusoïdaux qui peuvent
être activés ou désactivés séparément. S'ils sont activés l'un après l'autre,
on entend 3 sons indépendants. Si on change leur fréquence après les avoir
tous activés, alors on n'entend plus qu'un seul son :

<p>
<faust-editor>
<!--
import("stdfaust.lib");
f = hslider("freq",440,50,2000,0.01);
process = sum(i,3,os.osc(f*(i+1))*checkbox("%i on"))/3
    <: _,_; // stereo
-->
</faust-editor>
</p>

## Localisation

Pour estimer la direction d’une source, le cerveau compare les signaux reçus
par les deux oreilles :

- **différence de temps d’arrivée**, particulièrement utile dans le grave ;
- **différence de niveau**, particulièrement importante dans l’aigu.

La forme de la tête et des pavillons modifie également le spectre et aide à
distinguer l’avant, l’arrière et la hauteur d’une source. Les techniques 
« binaural » exploitent ces propriétés pour produire artificiellement un rendu 
sonore en 3 dimensions en utilisant un casque audio.

La vidéo suivante est un enregistrement binaural d'une coupe de cheveux chez un
coiffeur :

<center>
<iframe width="560" height="315" src="https://www.youtube.com/embed/waYCrToYVn0?si=5Hjo7T6GIlsG2ZEj" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</center>

## Précédence et réverbération

Dans une salle, le son direct est suivi de nombreuses réflexions. Lorsque les
réflexions arrivent peu après le son direct, elles ne sont pas nécessairement
perçues comme des sons séparés. C'est l'une des différence entre un echo et
une réverbération.

Le programme Faust suivant implémente 4 échos en parallèle avec des durées
différentes. Si ces dernières sont proches de 1 seconde, alors en entend bien
les échos individuels. À l'inverse, plus elles sont faible plus on entend un
effet de réverbération. 

<p>
<faust-editor>
<!--
import("stdfaust.lib");
d = hslider("delay",1,0,1,0.01);
process = _ <: par(i,4,ef.echo(1,d/(i+1),0.5)) :> _/4
    <: _,_; // stereo
-->
</faust-editor>
</p>
    
Le premier son arrivé détermine généralement la direction de la source. Les
réflexions contribuent à la sensation d’espace et de réverbération. C’est
l’**effet de précédence**.

## Illusions auditives

Les illusions révèlent les stratégies utilisées par le cerveau pour interpréter
le son.

### Battements entre fréquences proches

Deux sons avec une fréquence très proche l'une de l'autre produisent un effet de
« battement » : 

<p>
<faust-editor>
<!--
import("stdfaust.lib");
o = hslider("offset",0,0,40,1);
process = (os.triangle(440) + os.triangle(440 + o))/2
    <: _,_; // stereo
-->
</faust-editor>
</p>

Cet effet est connu des accordeurs de piano qui l'utilisent pour accorder les 
différentes cordes produisant le son d'un note.

### Son de Shepard

Les [sons de Shepard](https://fr.wikipedia.org/wiki/Gamme_de_Shepard) sont des
sons qui donnent l'impression de monter ou de descendre à l'infini :

<center>
<iframe width="560" height="315" src="https://www.youtube.com/embed/BzNzgsAE4F0?si=UClDvf-1pkiVhJIV" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</center>

Pour cela plusieurs oscillateurs sont placés en parallèle et prennent le relais
les uns sur les autres dans un mouvement ascendant ou descendant.

Cet effet a été exploité par le compositeurs Jean-Claude RISSET dans certains de
ses œuvres. 


<!--
## Activités

1. Tester la fondamentale absente.
2. Comparer la sonie de plusieurs fréquences à niveau identique.
3. Concevoir un exemple de masquage dans un arrangement musical.
4. Écouter une phrase monodique au sein d’une texture et identifier les indices
   permettant de la suivre.
5. Localiser des sons produits autour d’un auditeur ayant les yeux fermés.
-->

## À retenir

- La perception ne reproduit pas mécaniquement le signal physique.
- La hauteur peut être perçue même si sa fondamentale est absente.
- La sonie dépend du niveau, de la fréquence et du contexte.
- Un son peut en masquer un autre.
- L’attaque et l’évolution spectrale participent à la reconnaissance du timbre.
- Le cerveau regroupe, sépare et localise les événements sonores.

## Aller plus loin

Si la psychoacoustique vous intéresse, nous vous recommandons l'ouvrage 
« The psychology of Music » de Diana Deutsch.

<script src="https://cdn.jsdelivr.net/npm/@grame/faust-web-component@0.6.1/dist/faust-web-component.js"></script>
