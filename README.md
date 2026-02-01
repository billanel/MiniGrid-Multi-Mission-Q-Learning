# MiniGrid-Multi-Mission-Q-Learning

Un projet de reinforcement learning utilisant Q-Learning pour apprendre à naviguer dans des environnements MiniGrid avec plusieurs missions de couleurs différentes.

## 🎯 Description

Ce projet entraîne un agent à résoudre 4 missions différentes dans le même environnement MiniGrid 8x8:
- 🔴 **Red**: Aller vers la porte rouge
- 🟢 **Green**: Aller vers la porte verte
- 🔵 **Blue**: Aller vers la porte bleue
- 🟡 **Yellow**: Aller vers la porte jaune

L'agent apprend à distinguer les différentes missions et à trouver le chemin optimal pour chacune.

## 🚀 Installation

### Prérequis
- Python 3.8+
- pip

### Étapes

1. **Cloner le repository**
```bash
git clone https://github.com/votre-username/minigrid-qlearning.git
cd minigrid-qlearning
```

2. **Créer un environnement virtuel (recommandé)**
```bash
python -m venv venv
source venv/bin/activate  # Sur Windows: venv\Scripts\activate
```

3. **Installer les dépendances**
```bash
pip install -r requirements.txt
```

## 📝 Usage

### Entraînement avec logs
```bash
python src/train_4missions_perfect.py
```

Cela va:
- Entraîner l'agent sur 8000 épisodes
- Afficher les statistiques tous les 500 épisodes
- Sauvegarder les résultats d'entraînement

### Visualisation temps réel
```bash
python src/realtime.py
```

Affiche l'agent en action en naviguant dans l'environnement avec des délais pour mieux voir.

## 📊 Configuration

Les paramètres d'entraînement se trouvent en haut de chaque script:

```python
# Environnement
ENV_ID = "MiniGrid-GoToDoor-8x8-v0"
TRAIN_SEEDS = [3657, 8182, 9656, 10255]  # 4 graines pour les 4 missions

# Hyperparamètres
ALPHA = 0.1        # Taux d'apprentissage
GAMMA = 0.99       # Facteur d'actualisation
EPS_START = 1.0    # Exploration initiale
EPS_END = 0.05     # Exploration finale
EPS_DECAY = 0.9992 # Décroissance de l'exploration

# Entraînement
EPISODES = 8000
MAX_STEPS = 100
```

## 🧠 Architecture

### Fichiers principaux

- `src/train_4missions_perfect.py` - Script d'entraînement complet avec logging
- `src/realtime.py` - Visualisation en temps réel de l'agent
- `src/config.py` - Configuration centralisée (optionnel)

### Algorithme

**Q-Learning**: Apprentissage par renforcement hors-politique
- État = (position_x, position_y, direction, mission_id)
- Actions = [gauche, droite, avancer, terminer]
- Récompense = +1 pour succès, -1 pour pas inutile

## 📈 Résultats attendus

Après entraînement:
- L'agent devrait apprendre les 4 chemins différents
- Convergence vers des solutions quasi-optimales après ~4000 épisodes
- Temps de résolution : ~10-15 pas en moyenne par mission


## ⭐ Si vous aimez ce projet

N'hésitez pas à le star sur GitHub !
