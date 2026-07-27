# Acoustique architecturale

## Réverbération

<figure>
<img src="reponseSalle.jpg" class="mx-auto d-block" width="80%">
<figcaption><center><i>Réponse impulsionnelle d'une salle.</i></center></figcaption>
</figure>

La durée et la qualité de la réverbération dépendent des dimensions de la salle ainsi que des matériaux qui la recouvrent. Chaque matériau possède un coefficient d'absorption qui lui est propre :

<figure>
<img src="absoption.gif" class="mx-auto d-block" width="80%">
</figure>

L'absorption d'une salle (en m2) :

$$ 
A = S \times \alpha_{moy} 
$$ 

avec: 

$$
\alpha_{moy}
$$ 

le coefficient d'absoprtion moyen de la salle :

$$
\alpha_{moy} = \frac{1}{S_{Totale}}(\alpha_{1}S_{1} + \alpha_{2}S_{2} + \dots + \alpha_{n}S_{n})
$$

**Formule de Sabine :**

Le temps de réverbération :

$$
T_{60}
$$


(temps mis par le son pour décroître de 60 dB dans la salle après extinction de la source) :

$$
Tr = \frac{0.16V}{A}
$$

où *V* est le volume de la salle en m3.

## Fréquences propres d'une salle

Ce sont les fréquences de vibration naturelles de la salle.

Elles correspondent aux fréquences pour lesquelles existent des ondes stationnaires.

En considérant les parois réfléchissantes et parallèles, dans une salle parallélépipédique de dimensions X, Y et Z, il existe une infinités de modes propres selon les entiers l, m, n (≥ 0) :

$$
f_{l,m,n} = \frac{c}{2}\sqrt{ \left( \frac{l}{X} \right) ^2 + \left( \frac{m}{Y} \right) ^2 + \left( \frac{n}{Z} \right) ^2}
$$
