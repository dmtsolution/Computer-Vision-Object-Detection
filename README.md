# Détection d’Objets : Reconnaissance de Chats avec Faster R-CNN

Projet réalisé dans le cadre du module **Vision par Ordinateur**  
**Date** : 4 Janvier 2026  

## Auteurs

- **AKAKPO Mathieu**  
- **MINTSA-MI OBAME Dimitri**  
- **AGBEVIADE Joackim**

## Objectif du projet

Implémentation d’un modèle de **détection d’objets** pour identifier et localiser les chats dans des images complexes (présence de chiens, humains, occlusions, éclairages variés).  
Le modèle minimise les faux positifs tout en maintenant une haute précision de localisation.

## Modèle utilisé

- **Architecture** : Faster R-CNN avec backbone **ResNet-50-FPN V2**  
- **Base** : pré-entraîné sur COCO (TorchVision)  
- **Transfert learning** : tête de classification adaptée à **2 classes** (background + chat)  
- **Entraînement** : 20 epochs, batch size 8, optimiseur SGD, scheduler StepLR  
- **Datasets** :  
  - Oxford-IIIT Pet Dataset (chats regroupés en une classe, chiens extraits comme négatifs)  
  - Extraits MS COCO (humains + scènes sans animaux pour réduire les confusions)

## Performances (jeu de test, seuil optimal 0.8)

- **Précision** : 98.3 %  
- **Rappel** : 97.7 %  
- **F1-score** : 0.980  
- **IoU moyen** : 0.923  

Meilleur modèle sauvegardé à l’epoch 17 (plus basse validation loss).

