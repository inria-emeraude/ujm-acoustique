# Lab : Voix chantée 

La synthèse de la voix chantée est maîtrisée depuis de nombreuses années comme le montre les exemples fournis sur cette page : <http://recherche.ircam.fr/anasyn/peeters/PSOLA/voix2.html>

Le but de ce lab est d'implémenter un synthétiseur vocal en analysant des sons de voix enregistrés. 

## Détection de formants (10 pt)

Les 5 fichiers audio suivants contiennent l'enregistrement des 5 voyelles prononcées par une voix d'homme : [a.wav](../res/a.wav), [e.wav](../res/e.wav), [i.wav](../res/i.wav), [o.wav](../res/o.wav) et [u.wav](../res/u.wav).

Pour chacun d'entre-eux, mesurez la fréquence en le niveau dB des 4 premiers formants en utilisant l'outil `Analyze/Plot Spectrum` d'Audacity.

Consignez les valeurs dans un tableau.

## Synthétiseur vocal (10 pt)

Le programme Faust suivant permet de synthétiser des voyelles en utilisant un modèle source/filtre : un oscillateur en dent de scie jour le rôle des cordes vocales et 4 filtre de type passe bande, la cavité buccale. 

<p>
<faust-editor>
<!--
import("stdfaust.lib");

// vowel values
aFreq(i) = ba.take(i+1,(728,2653,3441,6417));
aDB(i) = ba.take(i+1,(-7.4,-33.8,-31.3,-62.1));
uFreq(i) = ba.take(i+1,(239,1821,2211,3151));
uDB(i) = ba.take(i+1,(-2.4,-18.7,-15.3,-23));

// change the vowel here
vowelFreq = aFreq;
vowelDB = aDB;

process = os.sawtooth(100) <: 
    par(i,4,fi.resonbp(vowelFreq(i),10,ba.db2linear(vowelDB(i)))) :> _/4
    <: _,_; // stereo
-->
</faust-editor>
</p>

Actuellement, la voyelle « a » est prononcée. 

Pour prononcer la voyelle « u », changez les deux lignes suivantes tel que :

```
vowelFreq = uFreq;
vowelDB = uDB;
```

Entendez-vous la différence ?

En utilisant les valeurs mesurées dans l'étape précédente, ajoutez les voyelles restantes (e, i, o) au programme en le modifiant. 

<script src="https://cdn.jsdelivr.net/npm/@grame/faust-web-component@0.6.1/dist/faust-web-component.js"></script>
