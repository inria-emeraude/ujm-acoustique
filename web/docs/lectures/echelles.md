# Les échelles musicales

<!-- TODO: il faudrait des exemples Faust pour bien faire -->

## Le tempérament égal

Dans la gamme à tempérament égal, le rapport de fréquence Fn / Fn-1 entre la fréquence Fn d'une note et la fréquence d'une note située un demi-ton au dessous Fn-1 est constant, quelle que soit la note considérée.

Sachant que le rapport Fn / Fn-12 entre la fréquence d'une note Fn et la fréquence d'une note située à l'octace en dessous (12 demi-tons plus bas) Fn-12 est égal à 2: on en déduit que le rapport de Fn / Fn-1 = 2 puissance 1/12 = 1.05946.

$$
F_{n+1} = F_{n} \times 2^{1/12}
$$

=> si La3 vaut 440 Hz, le La#3 vaut 440 x 1,05946 = 466,16 Hz.

$$
F_{n} = 440 \times 2^{(n-69)/12}
$$

=> sachant qu'en MIDI, la note 69 est le La3 dont la fréquence vaut 440 Hz.

## Les autres tempéraments

La musique est souvent construite à partir de sons ayant des hauteurs précises. Ces hauteurs sont souvent définies à partir des proportions liées à la succession des harmoniques à partir d'une note fondamentale ou tonique.

|  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| rapport de fréquence | 1 | 9/8 | 5/4 | 4/3 | 3/2 | 5/3 | 15/8 | 2 |
| intervalle | unisson | 2nde maj | 3ce maj | 4te juste | 5te juste | 6te maj | 7e maj | octave |
| note | La2 | Si2 | Do#3 | Ré3 | Mi3 | Fa#3 | Sol#3 | La3 |
| fréquence juste | 220 | 247,5 | 275 | 293,33 | 330 | 366,67 | 412,5 | 440 |
| tempérament égal | 220 | 246,94 | 277,18 | 293,66 | 329,63 | 369,99 | 415,3 | 440 |
| écart (en 1/2 ton) | 0,00 | 4% | 14% | 2% | 2% | 16% | 12% | 0,00 |
| f. pythagoricienne | 220 | 247,5 | 278,44 | 297,34 | 330 | 371,25 | 417,66 | 446 |
| f. pythog. corrigée | 220 | 247,5 | 278,44 | 297,34 | 330 | 371,25 | 417,66 | 440 |

### La gamme pythagoricienne

Elle est construite en utilisant le cycle des quintes :

do - sol - ré - la - mi - si - fa# - do# - sol# - ré# - la# - mi# (fa) - si# (do)

On appelle gamme pythagoricienne toute gamme musicale fondée uniquement sur des intervalles d'octaves et de quintes acoustiquement pures. Un telle gamme contient aussi des quartes pures, renversements des quintes.

La douzième quinte dépassant légèrement l'octave (d'un comma), elle va être réduite pour former l'octave juste. Cette quinte plus petite est inutilisable en musique car elle sonne faux. On dit qu'elle hurle, et se nomme « quinte du loup ». Dans la pratique, les musiciens qui utilisent une gamme pythagoricienne placent la quinte du loup dans un intervalle peu utilisé, comme par exemple sol# - mi#.

### La gamme de Zarlino

Avec le tempérament Zarlino, les principaux intervalles dans un mode donné (par exemple en do) correspondent à des rapports de fréquences qui correspondent à des fractions simples : do- ré = 9/8 (deux quintes pures transposées d’une octave : 3/2 × 3/2 ÷ 2), do-mib =  6/5 do-mi = 5/4, do - fa = 4/3, do = sol = 3/2, do - la = 5/3 (une tierce majeure + une quarte : 5/4 x 4/3 = 5/3), do-si = 15/8 (une tierce majeure + une quinte: 5/4 x 3/2 = 15/8).

<figure>
<img src="zarlino.png" class="mx-auto d-block" width="100%">
</figure>

### La gamme de Werckmeister III

Dans ce tempérament, le comma pythagoricien est réparti par quarts sur 4 quintes (qui deviennent ainsi un peu courtes) : do-sol, sol-ré, ré-la et si-solb.

Ainsi les tierces do-mi et fa-la sont assez proches d’intervalles justes, les autres s'en éloignant progressivement. Ce tempérament, par le choix de la quinte tempérée si-solb favorise les tonalités en bémol.

<figure>
<img src="werck3.png" class="mx-auto d-block" width="100%">
</figure>

<video width="100%" controls="controls">
  <source src="temperament.mp4" type="video/mp4">
</video>

<script src="https://cdn.jsdelivr.net/npm/@grame/faust-web-component@0.6.1/dist/faust-web-component.js"></script>
