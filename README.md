# Détection d'objets - Classes de personnages Dofus

Projet de détection et classification des 19 classes de personnages du MMORPG Dofus utilisant YOLOv11.

Ce projet applique des techniques de deep learning pour détecter et classifier automatiquement les différentes classes de personnages présentes dans des captures d'écran du jeu Dofus. Nous avons entraîné deux modèles YOLOv11 (Nano et Small) sur un dataset personnalisé d'images du jeu.


## Le jeu Dofus

Dofus est un MMORPG développé par Ankama, se déroulant dans un univers médiéval-fantastique. Le jeu propose **19 classes de personnages** distinctes, chacune avec ses propres caractéristiques visuelles et capacités.

## Dataset

- **Taille totale :** 603 images
- **Répartition :** 80% entraînement (483 images) / 10% validation (61 images) / 10% test (59 images)
- **Classes :** 19 classes de personnages Dofus
- **Source :** Captures d'écran réalisées en mode "créature" pour réduire les ambiguïtés visuelles

### Prétraitement des images

1. Suppression des bordures de l'interface utilisateur
2. Découpage en 4 parties égales pour augmenter la taille relative des objets
3. Tri et suppression des images sans personnages
4. Renommage selon une nomenclature standardisée

## Structure du projet

```
├── datasets/
│   ├── images/          # Images du dataset
│   └── labels/          # Annotations au format YOLO
├── yolo11n_dofus/       # Résultats du modèle YOLOv11 Nano
├── yolo11s_dofus/       # Résultats du modèle YOLOv11 Small
├── ImagesPreprocessing.ipynb  # Script de prétraitement des images
├── dataset.yaml         # Fichier de configuration YOLO
└── README.md
```

## Modèles entraînés

### YOLOv11 Nano
### YOLOv11 Small


## Résultats

Les deux modèles montrent d'excellentes performances :
- **14 classes sur 19** avec un taux de classification > 90% (modèle Nano)
- Le modèle Small apporte une amélioration générale des performances
- Quelques confusions persistent sur les classes sous-représentées

### Types d'erreurs observées
1. **Non-détection** de personnages avec faible contraste
2. **Faux positifs** sur des éléments du décor
3. **Confusion entre classes** similaires visuellement

## Outils utilisés

- **Annotation :** Roboflow (collaboration, stockage en ligne, génération automatique des sous-ensembles)
- **Modèle :** YOLOv11 (Nano et Small)
- **Langage :** Python
- **Paramètres d'entraînement :** 50 époques, batch size 50, taille d'image 512px

## Généralisation

Le modèle Small a été testé sur d'anciennes versions de Dofus :
- **Dofus 2.0 (2009-2024) :** Bonnes détections malgré des probabilités plus faibles
- **Dofus 1.29 (2004-2009) :** Performances réduites dues aux différences visuelles importantes

## Améliorations possibles

- Augmentation de la taille du dataset
- Meilleure représentativité des classes sous-représentées
- Test d'architectures plus larges (YOLOv11L, YOLOv11X)
- Exploration de YOLOv12
- Ajustement du seuil de confiance pour réduire les faux positifs

## Auteurs

- **EL HARRANI Abdelali**
- **PEYROUTON Clément**

*Mastère VALDOM 2025*
