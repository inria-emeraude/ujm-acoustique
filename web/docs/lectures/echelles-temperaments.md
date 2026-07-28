# Intervalles, gammes et tempéraments

<!--
## Objectifs

- relier les intervalles à des rapports de fréquences ;
- comprendre pourquoi plusieurs systèmes d’accordage sont possibles ;
- distinguer intonation juste, gamme pythagoricienne et tempérament égal ;
- écouter des différences d’accordage sans réduire la musique à des calculs.
-->

## Octave et rapports de fréquences

La sensation d’intervalle dépend principalement du rapport entre les fréquences.
Une octave correspond au rapport \(2/1\) :

- 110 Hz et 220 Hz ;
- 220 Hz et 440 Hz ;
- 440 Hz et 880 Hz.

Des rapports simples correspondent à plusieurs intervalles consonants :

| Intervalle | Rapport simple |
| --- | ---: |
| unisson | 1/1 |
| octave | 2/1 |
| quinte juste | 3/2 |
| quarte juste | 4/3 |
| tierce majeure juste | 5/4 |
| tierce mineure juste | 6/5 |

Ces rapports apparaissent dans la série harmonique, mais leur utilisation dans
une gamme complète soulève des difficultés : il n’est pas possible de conserver
tous les intervalles parfaitement purs dans toutes les tonalités avec un
système fixe de douze notes.

## Battements et justesse

Deux fréquences très proches produisent des variations périodiques d’amplitude
appelées **battements**. Plus les fréquences sont proches, plus les battements
sont lents (cf. [cours de psychoacoustique](psychoacoustique.md)).

Les musiciens utilisent souvent les battements pour ajuster un intervalle. Un
intervalle légèrement différent d’un rapport simple peut faire battre certains
harmoniques.

## Intonation juste (Zarlino)

Dans une [intonation juste](https://fr.wikipedia.org/wiki/Intonation_juste) (ou dite de « Zarlino »), les intervalles principaux d’une tonalité utilisent
des rapports simples.

Exemple d’une gamme majeure construite sur La :

| Degré | La | Si | Do♯ | Ré | Mi | Fa♯ | Sol♯ | La |
| --- | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| Rapport | 1 | 9/8 | 5/4 | 4/3 | 3/2 | 5/3 | 15/8 | 2 |
| Fréquence si La = 220 Hz | 220 | 247,5 | 275 | 293,3 | 330 | 366,7 | 412,5 | 440 |

et d'une gamme chromatique :

<figure>
<img src="../../res/zarlino.png" class="mx-auto d-block" width="100%">
</figure>

Ce système produit de très beaux accords dans certaines tonalités, mais ne
permet pas de moduler librement sans modifier l’accordage.

## Gamme pythagoricienne

La [gamme pythagoricienne](https://fr.wikipedia.org/wiki/Accord_pythagoricien) est construite à partir de quintes pures de rapport
\(3/2\) :

do – sol – ré – la – mi – si – fa♯ – do♯ – sol♯ – ré♯ – la♯ – mi♯

Après douze quintes, on ne retombe pas exactement sur la même fréquence qu’après
sept octaves. Le petit écart obtenu est le **comma pythagoricien**.

Dans un accordage fixe, cet écart doit être placé ou réparti. Si onze quintes
restent pures, la dernière devient très différente : c’est la **quinte du
loup**.

La gamme pythagoricienne favorise les quintes, mais ses tierces majeures sont
sensiblement plus larges que les tierces justes.

## Tempéraments inégaux

Les tempéraments répartissent les écarts entre plusieurs intervalles.
[Werckmeister III](https://en.wikipedia.org/wiki/Werckmeister_temperament), par exemple, réduit légèrement certaines quintes afin de
rendre davantage de tonalités utilisables.

<figure>
<img src="../../res/werck3.png" class="mx-auto d-block" width="100%">
</figure>

Les tonalités ne sont alors pas parfaitement équivalentes : certaines possèdent
des tierces plus pures, d’autres des intervalles plus tendus. Cette diversité
fait partie de la couleur musicale des tempéraments historiques.

## Tempérament égal

Dans le tempérament égal à douze demi-tons, l’octave est divisée en douze
intervalles égaux. Le rapport entre deux demi-tons successifs est :

$$
2^{1/12} \approx 1{,}05946
$$

La fréquence de la note suivante est donc :

$$
f_{n+1}=f_n \times 2^{1/12}
$$

Si La = 440 Hz, le La♯ suivant vaut environ :

$$
440 \times 2^{1/12} = 466{,}16\ \text{Hz}
$$

Avec la numérotation MIDI, où le La 440 Hz porte le numéro 69 :

$$
f_n = 440 \times 2^{(n-69)/12}
$$

Le tempérament égal rend toutes les tonalités transposables de manière
identique. En contrepartie, à l’exception de l’octave, ses intervalles ne sont
pas parfaitement purs.

## Accordage et pratique musicale

Un système d’accordage n’est pas seulement une table de fréquences. Dans la
pratique, les musiciens ajustent continuellement leur intonation selon :

- le contexte harmonique ;
- la fonction de la note dans l’accord ;
- le timbre ;
- le registre ;
- les autres musiciens ;
- les possibilités de l’instrument.

Les instruments à hauteur libre peuvent adapter les intervalles. Les
instruments à clavier imposent généralement un accordage préparé à l’avance.
Dans un ensemble, plusieurs logiques d’intonation peuvent donc coexister.

<!--
## Activités

1. Écouter et comparer une tierce majeure juste et tempérée.
2. Faire apparaître des battements entre deux fréquences voisines.
3. Comparer une cadence dans plusieurs tempéraments.
4. Discuter l’accordage dans un quatuor à cordes, un chœur et un ensemble avec
   piano.
-->
   
## À retenir

- Les intervalles correspondent à des rapports de fréquences.
- Les rapports simples sont liés à la consonance et à la série harmonique.
- Aucun accordage fixe à douze notes ne conserve tous les intervalles purs.
- Les tempéraments réalisent des compromis différents.
- Le tempérament égal facilite la modulation, mais tempère presque tous les
  intervalles.

<script src="https://cdn.jsdelivr.net/npm/@grame/faust-web-component@0.6.1/dist/faust-web-component.js"></script>
