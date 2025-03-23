# PixelCNN: Modèles Autoregressifs pour la Génération d'Images

Les modèles autoregressifs sont des modèles génératifs qui apprennent à modéliser la distribution de données complexes, comme une image, en prédisant chaque composant d'une séquence en fonction des éléments précédents. Dans le cas de PixelCNN, l'objectif est de générer une image pixel par pixel en modélisant la distribution de probabilité conditionnelle de chaque pixel par rapport aux pixels déjà générés.

## Architecture

- **Masked Convolution Layers** :  
  Empêche le modèle d’accéder aux pixels qui n’ont pas encore été générés, assurant le caractère autoregressif.  
  - **Type A** : Pour la première couche, exclut le pixel en cours de génération.  
  - **Type B** : Pour toutes les autres couches, donne accès au pixel généré.
 
    ![image](https://github.com/user-attachments/assets/7d0280e1-dabb-4d40-81f4-d27f00526104)

  Avec \( K \) le noyau de convolution, \( M \) le masque et \( X \) l’image d'entrée.

- **Residual Block** :  
  Améliore la stabilité et la performance du modèle grâce aux **skip connections**, permettant de « sauter » certaines couches et de répondre au problème de **vanishing gradient**.

Le PixelCNN repose sur un empilement de **masked convolution layers** et de **residual blocks**, suivi d’une couche de sortie qui prédit la distribution de probabilité du prochain pixel à l'aide de la fonction **softmax**.

## Fonctionnement

1. **Préparation de la donnée** :  
   Redimensionnement du **Fashion MNIST Dataset**.

2. **Entraînement** :  
   Pour chaque image, le modèle prédit la distribution de probabilité conditionnelle de chaque pixel en fonction des pixels précédents.

3. **Utilisation du Cross-Entropy Loss** :  
   Calcul de la perte entre les prédictions et les valeurs réelles des pixels.
   
   ![image](https://github.com/user-attachments/assets/bcfbcf3f-a9f8-4bc5-9c1f-ce442bd9ebd7)

5. **Optimisation** :  
   Utilisation de l'optimiseur **Adam** pour ajuster les paramètres du modèle.

## Conclusion

PixelCNN est un modèle autoregressif efficace pour générer des images pixel par pixel. Grâce à ses **convolutions masquées** et ses **blocs résiduels**, il capture les dépendances locales entre les pixels tout en restant stable à l'entraînement. Ses applications incluent la génération d'images, la compression, la complétion et la super-résolution. Polyvalent et performant, PixelCNN est un outil clé pour la modélisation et la création d'images réalistes.
