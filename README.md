# Masques Detection

## Images

La première étape consistait à réaliser notre dataset Train et Test. Après avoir affilié la direction des fichiers without_mask et with_mask des train et test, nous avons pu créer nos listes. Chaque image des dossiers a été associée à leur label (pour y) without_mask = 0 et with_mask = 1.

La deuxième étape était de préparer les images pour l'entrainement de notre modèle. Nous avons donc resize en 96x96 pixels les images puis reshape nos données x_app (train) en [-1, 96, 96, 3] (images en couleur).

Ce modèle contient 3 couches avec une activation par défaut reLu sur les deux premières et une activation sigmoid sur la dernière couche. La fonction loss *binary_crossentropy* a été choisie par défaut, et utilisée pour les problèmes de classification binaire où les valeurs cibles sont dans l'ensemble [0, 1] (without_mask, with_mask ici).

L'évaluation de notre modèle sur les données tests se présente ainsi : `loss: 0.1914 - accuracy: 0.9692`

Sur la matrice de confusion : Notre modèle classe correctement 189 images de notre dataset test (94 pour la classe sans masque = 0 ; 95 pour la classe avec masque = 1). Seul 6 images ne sont pas définies correctement par notre modèle (4 images sans masque sont considérés comme représentant des personnes avec des masques, et inversement, 2 images représentant des gens avec masques sont considérés sans masque).

Nous avons ensuite testé sur d'autres images.

## Vidéo

Nous avons testé notre modèle en vidéo. Un émoticone s'affiche si on porte ou non un masque. Un fichier audio s'active lorsque nous ne possédons pas de masque.
