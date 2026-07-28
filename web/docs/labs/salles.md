# Lab : Acoustique des salles

## Mesure de réponse impulsionnelle (12 pt)

En utilisant un enregistreur et le procédé étudié en cours basé sur l'explosion d'un ballon, enregistrez la réponse impulsionnelle stéréo de votre salle favorite :).

Une fois l'enregistrement effectué, normalisez le dans Audacity à -1 dB (`Effect/Volume and Compression/Normalize`) et supprimez les parties de l'enregistrement potentiellement inutiles (le son au début et à la fin).

## Réverbération artificielle (5 pt)

Le patch PlugData suivant : [conv.zip](../res/conv.zip) permet de convoluer un signal d'entrée avec une réponse impulsionnelle (ici `sdf.wav`).

Remplacez `sdf.wav` dans le patch avec la réponse impulsionnelle que vous avez mesuré et écoutez le résultat.

## Réverbération artificielle stéréo (3 pt)

Tentez de modifier le patch PlugData de l'étape précédente pour que la convolution se fasse en stéréo avec votre réponse impulsionnelle stéréo. 

<script src="https://cdn.jsdelivr.net/npm/@grame/faust-web-component@0.6.1/dist/faust-web-component.js"></script>
