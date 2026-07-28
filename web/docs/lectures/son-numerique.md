# Le son numérique

<!--
## Objectifs

À la fin de cette séance, les étudiants devront pouvoir :

- expliquer comment un signal continu est représenté par une suite de nombres ;
- distinguer fréquence d’échantillonnage et profondeur de quantification ;
- appliquer le théorème de Nyquist-Shannon à un signal simple ;
- reconnaître et expliquer le phénomène d’aliasing ;
- relier profondeur en bits, bruit de quantification et dynamique ;
- distinguer format PCM, format de fichier et compression avec ou sans perte.
-->

## Du son acoustique au signal numérique

Un microphone transforme les variations de pression acoustique en une tension
électrique continue. 

<figure>
<img src="../../res/analog.jpg" class="mx-auto d-block" width="100%">
<figcaption><center><i>Passage d'un son à un signal électrique et vice versa.</i></center></figcaption>
</figure>

Pour enregistrer ce signal dans un ordinateur, un
convertisseur analogique-numérique réalise deux opérations :

1. il mesure l’amplitude du signal à intervalles réguliers :
   **l’échantillonnage** ;
2. il remplace chaque mesure par une valeur choisie parmi un nombre fini de
   possibilités : **la quantification**.

<figure>
<img src="../../res/sampling.png" class="mx-auto d-block" width="80%">
<figcaption><center><i>Représentation d'un signal échantilloné (source : <a href="https://en.wikipedia.org/wiki/Sampling_(signal_processing)">Wikipedia</a>).</i></center></figcaption>
</figure>
   
Le résultat est une suite de nombres appelés **échantillons**.

<center>
```text
pression acoustique → microphone → signal électrique → 
conversion analogique-numérique → suite d’échantillons
```
</center>

Lors de la lecture, un convertisseur numérique-analogique effectue l’opération
inverse. Il transforme la suite d’échantillons en une tension continue envoyée
à un amplificateur puis à un haut-parleur.

## L’échantillonnage

La **fréquence d’échantillonnage**, notée \(f_s\), est le nombre de
mesures effectuées chaque seconde.

Quelques valeurs courantes :

| Fréquence | Usage fréquent |
| ---: | --- |
| 44,1 kHz | CD et diffusion musicale |
| 48 kHz | vidéo, audiovisuel et production |
| 88,2 ou 96 kHz | production en haute résolution |
| 192 kHz | usages spécialisés, mesure et archivage |

À 48 kHz, le convertisseur produit 48 000 échantillons par seconde et par
canal. La durée entre deux échantillons est :

$$
T_s = \frac{1}{f_s}
$$

À 48 kHz :

$$
T_s = \frac{1}{48000} \approx 20{,}8\ \mu s
$$

Une fréquence d’échantillonnage plus élevée augmente la fréquence maximale que le
système peut représenter.

## Le théorème de Nyquist-Shannon

Pour pouvoir reconstruire un signal limité en fréquence, sa fréquence
d’échantillonnage doit être strictement supérieure au double de sa fréquence la
plus élevée :

$$
f_s > 2f_{max}
$$

La moitié de la fréquence d’échantillonnage est appelée **fréquence de
Nyquist** :

$$
f_N = \frac{f_s}{2}
$$

Avec un échantillonnage à 44,1 kHz, la fréquence de Nyquist est de 22,05 kHz.
Cette valeur est légèrement supérieure à la limite haute conventionnelle de
l’audition humaine, située autour de 20 kHz chez un sujet jeune.

Le théorème ne signifie pas que deux points suffisent toujours pour dessiner
visuellement une belle sinusoïde. Il affirme qu’un signal limité à moins de
\(f_s/2\) peut, en théorie, être reconstruit à partir de ses échantillons grâce
à un filtrage approprié.

## L’aliasing ou repliement spectral

Si une composante du signal dépasse la fréquence de Nyquist, elle est
interprétée comme une autre fréquence située sous cette limite. Ce phénomène
irréversible est appelé **aliasing** ou **repliement spectral**.

En vidéo, on a l'habitude d'observer de l'aliasing :

<center>
<iframe width="560" height="315" src="https://www.youtube.com/embed/ByTsISFXUoY?si=0jJnRduCExycrbgs" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</center>

En audio, la fréquence repliée peut être déterminée en recherchant la distance de la
fréquence originale au multiple de \(f_s\) le plus proche :

$$
f_{alias} = |f - kf_s|
$$

où \(k\) est choisi pour que \(f_{alias}\) se trouve entre 0 et \(f_s/2\).

### Exemples à 44,1 kHz

- 20 kHz reste 20 kHz : cette fréquence est sous Nyquist ;
- 24,1 kHz est repliée à \(44,1-24,1=20\) kHz ;
- 30 kHz est repliée à \(44,1-30=14,1\) kHz ;
- une sinusoïde à 44,1 kHz produit toujours la même valeur aux instants
  d’échantillonnage et apparaît donc à 0 Hz.

L’aliasing ne concerne pas seulement l’enregistrement. Il peut être produit à
l’intérieur d’un synthétiseur ou d’un effet numérique par des opérations
non linéaires : saturation, distorsion, modulation ou génération de formes
d’onde riches en harmoniques.

### Démonstration Faust

Le programme suivant permet d’augmenter la fréquence d’une sinusoïde jusqu’à la
fréquence d’échantillonnage. Au-delà de Nyquist, la hauteur perçue redescend :

<p>
<faust-editor>
<!--
import("stdfaust.lib");
frequency = hslider("frequency[unit:Hz]",440,20,ma.SR,1);
gain = 0.1;
process = os.osc(frequency)*gain;
-->
</faust-editor>
</p>

> **À écouter :** repérer la fréquence à laquelle le mouvement ascendant
> s’inverse. Elle dépend de la fréquence d’échantillonnage du système.

## Le filtre anti-repliement

Avant l’échantillonnage, un **filtre anti-repliement** atténue les fréquences
supérieures à la fréquence de Nyquist. Sans ce filtre, des ultrasons ou du bruit
haute fréquence pourraient créer des composantes audibles artificielles après
conversion.

<!--
Un filtre réel ne coupe pas instantanément toutes les fréquences à une limite
précise. Il possède une bande de transition. Les convertisseurs modernes
utilisent souvent une fréquence interne beaucoup plus élevée que la fréquence
finale : c’est le **suréchantillonnage**. Cette technique facilite le filtrage
avant de ramener le signal à 44,1 ou 48 kHz.
-->

Lors de la conversion numérique-analogique, un **filtre de reconstruction**
supprime les images spectrales produites par la restitution des échantillons.

## La quantification

Après l’échantillonnage temporel, chaque amplitude doit être représentée par un
nombre fini de valeurs.

Avec une quantification sur \(N\) bits, le nombre de valeurs disponibles est :

$$
2^N
$$

| Profondeur | Nombre de valeurs |
| ---: | ---: |
| 8 bits | 256 |
| 16 bits | 65 536 |
| 24 bits | 16 777 216 |

La valeur mesurée se trouve rarement exactement sur un niveau disponible. Elle
est arrondie : la différence entre la valeur originale et la valeur retenue est
l’**erreur de quantification**.

Cette erreur se manifeste généralement comme un bruit, mais à très faible
niveau elle peut devenir corrélée au signal et produire une distorsion.

### Démonstration Faust

Le programme suivant réduit artificiellement le nombre de niveaux disponibles :

<p>
<faust-editor>
<!--
import("stdfaust.lib");
steps = nentry("quantization steps",256,1,65536,1);
frequency = hslider("frequency[unit:Hz]",440,50,2000,1);
quantize(x) = floor(x*steps+0.5)/steps;
process = os.osc(frequency)*0.8 : quantize;
-->
</faust-editor>
</p>

> **À écouter :** comparer 65 536 niveaux, correspondant approximativement à
> 16 bits, avec 256, 16 puis 4 niveaux.

## Profondeur en bits et dynamique

Pour un signal sinusoïdal correctement quantifié, le rapport signal-bruit
théorique d’un système PCM linéaire est approximativement :

$$
SNR \approx 6{,}02N + 1{,}76\ \text{dB}
$$

On retient souvent la règle simplifiée : **un bit supplémentaire apporte
environ 6 dB de dynamique**.

| Profondeur | Dynamique théorique approximative |
| ---: | ---: |
| 8 bits | 50 dB |
| 16 bits | 98 dB |
| 24 bits | 146 dB |

Les convertisseurs 24 bits réels n’atteignent généralement pas 146 dB, car le
bruit de leurs composants analogiques devient limitant. Le 24 bits reste
néanmoins utile en production : il permet d’enregistrer avec une marge de
sécurité importante sans rapprocher le signal du bruit de quantification.

La profondeur en bits ne fixe pas le niveau maximal produit par les enceintes.
Elle décrit la précision et la plage dynamique de la représentation numérique.

## PCM, formats et compression

Le **PCM** (*Pulse Code Modulation*) est la représentation directe d’une suite
d’échantillons quantifiés. Un fichier audio doit également stocker des
informations telles que :

- la fréquence d’échantillonnage ;
- la profondeur en bits ou le format des nombres ;
- le nombre de canaux ;
- l’ordre et l’organisation des données.

### Formats non compressés

- WAV et AIFF contiennent couramment de l’audio PCM ;
- ils peuvent utiliser différentes fréquences et profondeurs ;
- le nom du conteneur ne suffit donc pas à connaître la résolution.

### Compression sans perte

FLAC et ALAC réduisent la taille sans supprimer d’information. Après
décompression, les échantillons sont identiques à ceux du fichier PCM original.

### Compression avec perte

MP3, AAC ou Opus suppriment des informations jugées moins audibles à l’aide de
modèles psychoacoustiques. La qualité dépend notamment :

- du codec ;
- du débit binaire ;
- de la complexité du signal ;
- du nombre de générations de compression.

La fréquence d’échantillonnage, la profondeur en bits et le débit compressé
sont donc trois grandeurs différentes.

## Taille d’un fichier PCM

Pour un signal PCM non compressé :

$$
\text{taille} =
\text{durée} \times f_s \times
\text{nombre de bits} \times
\text{nombre de canaux}
$$

Pour une minute stéréo à 44,1 kHz et 16 bits :

$$
60 \times 44100 \times 16 \times 2
= 84\,672\,000\ \text{bits}
$$

soit environ 10,6 Mo en utilisant 8 bits par octet, avant les quelques octets
de métadonnées du fichier.

## Pourquoi travailler à 48 ou 96 kHz et en 24 bits ?

Une fréquence de 44,1 ou 48 kHz suffit à représenter le domaine audible lorsque
la conversion est correctement réalisée. Des fréquences plus élevées peuvent
toutefois être utiles :

- filtres de conversion plus faciles à concevoir ;
- traitement de signaux destinés à être ralentis ;
- réduction de l’aliasing dans certains effets non linéaires ;
- besoins de mesure ou de recherche.

Elles augmentent aussi la quantité de données, la charge de calcul et parfois
la latence.

Le 24 bits est particulièrement utile pendant l’enregistrement et le mixage
pour conserver une grande marge dynamique. La qualité finale ne dépend cependant
pas uniquement des nombres annoncés : prise de son, traitement, écoute et
maîtrise des niveaux restent déterminants.

## Premier soun synthétisé par un ordinateur

Les techniques d'échantillonage ont été formalisée dans les années 1920 et 1930
mais ce n'est qu'en 1958 qu'elles furent mises en application pour synthétiser
un son avec un ordinateur par Max Mathews aux Bell Labs (USA). Ce travail a
permis quelques années plus tard en 1962 de faire « chanter » l'ordinateur
pour la première fois :

<center>
<iframe width="560" height="315" src="https://www.youtube.com/embed/41U78QP8nBk?si=1mkasDsQcQEy_CKi" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</center>

Stanley KUBRICK fait un clin d'œil à Max Mathews dans *2001 : l'odysée de l'espace* :

<center>
<iframe width="560" height="315" src="https://www.youtube.com/embed/E7WQ1tdxSqI?si=uNNyAL2R0xrLvKKc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
</center>

## À retenir

- L’échantillonnage discrétise le temps ; la quantification discrétise
  l’amplitude.
- La fréquence maximale représentable est inférieure à \(f_s/2\).
- Une composante supérieure à Nyquist crée de l’aliasing.
- Le filtre anti-repliement empêche ces composantes d’entrer dans le signal
  numérique.
- Chaque bit supplémentaire apporte approximativement 6 dB de dynamique.
- Le dither transforme une distorsion de quantification en bruit aléatoire.
- Fréquence d’échantillonnage, profondeur en bits et débit compressé décrivent
  des propriétés différentes.

<script src="https://cdn.jsdelivr.net/npm/@grame/faust-web-component@0.6.1/dist/faust-web-component.js"></script>

