# The VOID - Guide d'utilisation
**The VOID** est un outil de **chiffrement** de commande conçu pour protéger vos messages. Ce guide présente uniquement les étapes d'installation et d'utilisation, sans entrer dans les détails du mécanisme de chiffrement.

## 📋 Table des matières

- Prérequis

- Installation

- Structure du projet

- Utilisation (CLI)

- Exemple d'exécution

- Organisation des fichiers générés

- Personnalisation de la base de données

- Licence

## 🔧 Prérequis

- **Python** 3.7 ou supérieur

Modules standards : os, json, csv, base64, random

Fichier db_updated.csv à la racine du projet

## 🚀 Installation

**1. Cloner le dépôt :**

git clone https://github.com/votre-utilisateur/the-void.git
cd the-void

**2. (Optionne) Environnement virtuel :**

python3 -m venv venv
source venv/bin/activate

**3.** Vérifiez la présence de db_updated.csv.

## 🗂 Structure du projet
the-void/
├── cryptographie_avancee.py   # Script principal CLI
├── db_updated.csv            # Base de données des tokens
├── keys/                     # Clés & métadonnées (.key)
└── tokens/                   # Messages chiffrés (.tokens)

## 💻 Utilisation (CLI)

Lancez le script :

python cryptographie_avancee.py

Vous accédez à un menu :

=== Bienvenu sur la cryptographie The VOID ===
+---------------------------+
| 1. Chiffrer un message    |
| 2. Déchiffrer un message  |
| 3. Quitter                |
+---------------------------+


**1. Chiffrer** : tapez 1, entrez votre texte, puis un nom de base pour générer :

- tokens/<nom>.tokens

- keys/<nom>.key

**2. Déchiffrer** : tapez 2, entrez le nom de base utilisé précédemment. Le message original s’affiche.

**Quitter** : tapez 3.

## 🖥 Exemple d'exécution

$ python cryptographie_avancee.py
Choix: 1
Entrez le message à chiffrer: Bonjour le monde
Nom de base des fichiers: mon_secret
-> Fichiers générés:
   - tokens/mon_secret.tokens
   - keys/mon_secret.key

$ python cryptographie_avancee.py
Choix: 2
Nom de base des fichiers: mon_secret
Message déchiffré: Bonjour le monde


## 📂 Organisation des fichiers générés

- **tokens/** : fichiers .tokens contenant le texte chiffré.

- **keys/** : fichiers .key (JSON) avec les métadonnées nécessaires.

**Remarque** : après un déchiffrement réussi, les fichiers .tokens et .key sont automatiquement supprimés.

## 🛠 Personnalisation de la base de données

db_updated.csv doit comporter :

| Colonne     | Description |
| ---      | ---       |
| dimension | taille du segment (NxN) |
| element_id | identifiant token (4 chiffres) |


## 📜 Licence

Ce projet est distribué sous licence MNMN. Voir LICENSE pour plus de détails.
