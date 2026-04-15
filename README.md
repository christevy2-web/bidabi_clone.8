# bidabi-clone-adapt-create
# BIDABI : Clone → Adapt → Create

Dépôt pédagogique du cours **Big Data and Business Intelligence (BIDABI)**.  
Ce projet a pour objectif d’initier les étudiants au travail avec du code open‑source, à l’adaptation de projets existants et à la création de leur propre jeu de données d’images.

## 🎯 Objectif du dépôt
Ce dépôt sert de **plateforme d’apprentissage** où les étudiants réalisent un cycle complet de travail en data et en machine learning :

- cloner un projet open‑source depuis GitHub
- analyser sa structure, ses dépendances et son fonctionnement
- adapter le code à un nouveau contexte
- créer un jeu de données d’images personnalisé
- intégrer ce jeu de données dans un pipeline ML existant

L’objectif est de reproduire des situations réelles rencontrées par les ingénieurs data et ML lorsqu’ils doivent réutiliser et modifier du code provenant d’autres développeurs.

## 🎓 Public visé
Ce projet est destiné aux étudiants du cours **BIDABI**, notamment ceux qui s’intéressent à :

- l’apprentissage automatique
- l’ingénierie des données
- la reproductibilité des expériences
- l’utilisation de GitHub et des projets open‑source

## 🧩 Contenu du dépôt
Le dépôt inclura :

- des exemples de code à analyser et adapter
- un modèle de structure pour le jeu de données
- des consignes pour les travaux pratiques
- des instructions pour exécuter et modifier le projet

## 🛠️ Compétences développées
Les étudiants apprendront à :

- lire et comprendre du code écrit par d’autres
- manipuler des dépôts GitHub
- concevoir et organiser un jeu de données d’images
- intégrer des données dans un pipeline ML
- documenter leur travail de manière claire et reproductible

## 📄 Licence et usage
Ce dépôt est destiné **exclusivement à des fins pédagogiques** dans le cadre du cours BIDABI.  
Le code et les ressources peuvent être simplifiés ou modifiés pour faciliter l’apprentissage.

---
---
## 📌 Vérification de l’exécution du projet
Ce document décrit les étapes nécessaires pour exécuter le projet de classification d’images basé sur ResNet‑18, directement depuis Visual Studio Code (VS Code) dans un environnement GitHub Codespaces.

### 🗂️ 1. Préparer la structure du projet
Le projet doit contenir les dossiers suivants :

```
project-root/
    src/
        classificator.py
    data/
        class01/
        class02/
        class03/
    .venv/
```
Le dossier data/ contient les sous‑dossiers correspondant aux classes.

Chaque sous‑dossier contient des images .jpg, .jpeg ou .png.

### 📦 2. Installer les dépendances dans l’environnement virtuel
Dans le terminal intégré de VS Code :

```
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cpu
pip install scikit-learn seaborn matplotlib umap-learn
```
Ces bibliothèques sont nécessaires pour l’entraînement, l’évaluation et les visualisations (t‑SNE, UMAP, ROC, etc.).

### 🧪 3. Vérifier que VS Code utilise le bon interpréteur Python
Dans VS Code :

Ouvrir la palette de commandes : Ctrl+Shift+P

Choisir : Python: Select Interpreter

Sélectionner l’environnement :

```
.venv/bin/python
```
### ▶️ 4. Lancer le script d’entraînement
Depuis la racine du projet :

```
python src/classificator.py
```
Si tout est correctement configuré, l’exécution affiche :

* les classes détectées dans data/
* la répartition Train / Val / Test
* les époques d’entraînement
* l’early stopping éventuel
* les métriques finales
* les visualisations (loss, accuracy, ROC, t‑SNE, UMAP, hardest samples)

Exemple :

```
Catégories détectées : ['class01', 'class02', 'class03']
Train: 5, Val: 1, Test: 3
Utilisation de l'appareil: cpu
Epoch 1/20 — Train Loss: ...
```
### 🧹 5. Résolution des erreurs fréquentes
```
❗ « FileNotFoundError: ./data/ »
```
Créer le dossier data/ à la racine du projet.
```
❗ « Number of classes does not match target_names »
```
Ajouter le paramètre labels= dans classification_report lorsque le dataset est très petit.

### 🎉 6. Résultat attendu
À la fin de l’exécution, le projet :

* entraîne un modèle ResNet‑18 avec MixUp
* sauvegarde le meilleur modèle
* génère toutes les métriques avancées
* produit les visualisations (confusion matrix, ROC, t‑SNE, UMAP)
* identifie les images les plus difficiles (hardest samples)
