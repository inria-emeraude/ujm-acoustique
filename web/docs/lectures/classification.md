## Classification des sons

Il existe différentes classifications des sons. Nous nous limiterons à la
suivante, on peut classer les sons en deux catégories : les sons élémentaires
et les sons complexes.

## Sons élémentaires

### L'impulsion

L'impulsion est un son de durée infiniment courte (clic ou impulsion ou dirac) comme un clap de cinéma ou un coup de révolver ou, en numérique, la succession 0, 1, 0 ou 0, 1, -1, 0. Certains acousticiens prétendent que ce son contient toutes les fréquences mais nous dirons plus simplement qu'il n'en contient aucune.

Le programme Faust suivant produit une impulsion une fois par seconde (à une période *p* correspondant au taux d'échantillonnage `ma.SR`) : 

<p>
<faust-editor>
<!--
import("stdfaust.lib");
p = ma.SR;
process = ba.pulse(p);
-->
</faust-editor>
</p>

### Le mouvement harmonique simple

Le mouvement harmonique simple (aussi appelé "son pur") correspond à une onde sinusoïdale de fréquence fixe. Le son produit par un diapason est proche d'un mouvement harmonique simple.

Le programme Faust suivant produit une sinusoïde à 440 Hz ce qui correspond un à LA3 :

<p>
<faust-editor>
<!--
import("stdfaust.lib");
f = 440;
process = os.osc(f);
-->
</faust-editor>
</p>

## Sons complexes

Les sons complexes correspondent à tous les autres sons. Ce sont donc des sons formés de la juxtaposition de plusieurs vibrations élémentaires (les sons partiels). Nous pouvons distinguer trois catégories: les sons harmoniques, les sons inharmoniques et les bruits.

### Les sons harmoniques

Ce sont des sons dont les partiels sont tous multiples d’une même fréquence fondamentale. Ce sont des sons à hauteur déterminée. Ils résultent d’une onde périodique.

Des partiels dont les fréquences sont en rapports harmoniques fournissent un ensemble particulier d'intervalles par rapport à notre perception musicale

<figure>
<img src="harmonics.gif" class="mx-auto d-block" width="60%">
<figcaption><center><i>Partiels harmoniques d'une fondamentale de fréquence f = 65.4 Hz (do-1) (en notation tempérée).</i></center></figcaption>
</figure>

Le programme Faust suivant implémente une suite harmonique constituée de sinusoïdes dont les fréquences sont toutes des multiples de la fondamentale :

<p>
<faust-editor>
<!--
import("stdfaust.lib");
fundamental = hslider("fundamental",300,50,2000,1);
nHarmonics = 5;
process = sum(i,nHarmonics,os.osc(fundamental*(i+1)))/nHarmonics;
-->
</faust-editor>
</p>

<figure>
<img src="mode2.gif" class="mx-auto d-block" width="60%">
<figcaption><center><i>Vibration d’une corde pincée dans ses modes de résonance secondaires.</i></center></figcaption>
</figure>

### Les sons inharmoniques

Ce sont des sons dont les partiels (identifiables à l'analyse) ne sont pas multiples (par ex. les sons de cloches).

Le programme Faust suivant produit un son inharmonique en ajoutant plusieurs sinusoïdes entre-elles dont les fréquences ne sont pas des multiples de la fondamentale :

<p>
<faust-editor>
<!--
import("stdfaust.lib");
fundamental = hslider("fundamental",300,50,2000,1);
nHarmonics = 5;
process = sum(i,nHarmonics,os.osc(fundamental+(i*53)))/nHarmonics;
-->
</faust-editor>
</p>

### Les bruits

Ce sont les sons dont le nombre de partiels est trop important pour qu'on puisse les identifier à l'analyse (ex. une cymbale, une caisse claire avec timbre) ou qui varient trop vite dans le temps.

Le programme Faust suivant produit du bruit blanc (un bruit dont la quantité d'énergie est la même sur l'ensemble du spectre) :

<p>
<faust-editor>
<!--
import("stdfaust.lib");
process = no.noise;
-->
</faust-editor>
</p>

Certains bruits ont un spectre non neutre, c'est le cas par exemple du « bruit rose » qui a un spectre plus « coloré » que celui du bruit blanc :

<p>
<faust-editor>
<!--
import("stdfaust.lib");
process = no.pink_noise;
-->
</faust-editor>
</p>

<script src="https://cdn.jsdelivr.net/npm/@grame/faust-web-component@0.6.1/dist/faust-web-component.js"></script>
