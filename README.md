# 🧪 Projet de Cryptographie Avancée – The Void & Curvax

Bienvenue dans ce projet combiné de **cryptographie avancée**, conçu pour explorer deux approches complémentaires de sécurisation des messages :  

- **🔮 The Void** – un système de **chiffrement invisible** basé sur Unicode et des substitutions spéciales.  
- **🔐 Curvax** – un système de **cryptographie asymétrique** basé sur des courbes mathématiques, du hachage et du bruit aléatoire.

---

## 🌌 Partie 1 : The Void – Chiffrement Invisible

### 🧠 Concept

**The Void** est un système de chiffrement **stéganographique** : les messages chiffrés ne laissent **aucune trace visible**. Il repose sur des caractères Unicode invisibles (espaces spéciaux, caractères de contrôle) pour représenter chaque caractère du message d'origine, rendant le texte chiffré **invisible à l'œil nu**.

### ⚙️ Fonctionnement

1. **Conversion** du message en indices basés sur un alphabet étendu (lettres, accents, chiffres, symboles…).
2. **Encodage** des indices sous forme de motifs Unicode invisibles.
3. **Décodage** réversible avec la clé fournie.

### 🔐 Sécurité

- Chaque message est encodé avec une **clé de permutation**.
- Possibilité de **segmenter** le message chiffré et d'ajouter un encodage spécial.
- Utilisation facultative de **fichiers `.tokens`** et de **fichiers de clés `.key.json`**.

### 📁 Exemple

```text
Message : Bonjour Élodie 💌
→ Chiffrement invisible (caractères Unicode spéciaux)
→ Texte apparemment vide mais contenant l'information
📦 Fichiers générés
.tokens : contient les séquences invisibles

.key.json : contient la clé d'encodage/décodage utilisée

🚧 Limites
L'encodage invisible peut être supprimé par des traitements automatiques (copier/coller, messageries…).

Le système repose sur des alphabets personnalisés : bien tester avant utilisation dans un environnement tiers.

🔐 Partie 2 : Curvax – Cryptographie Asymétrique Complexe
🧠 Concept
Curvax est un système de chiffrement asymétrique (à clé publique/clé privée) utilisant une courbe personnalisée pour transformer les caractères. Il introduit une complexité mathématique, du hachage et des coefficients aléatoires pour sécuriser les messages.

🧬 Détail technique
La courbe est définie ainsi :

python
Copier
Modifier
f(x) = x^3 + a·x² + b·x + hash(x,a,b) + sin(x)
Le résultat est pris modulo p (nombre premier).

🔑 Clés
Clé privée : (a, b, p)

Clé publique : (p, [(x, y)]) — points générés pour chaque caractère imprimable (ASCII 32–126)

🔒 Chiffrement
Pour chaque caractère :

x = ord(c)

y = courbe(x)

Choix aléatoire d’un coefficient n

Calcul du point chiffré :
y_complex = (y * n + n^2) % p

Résultat : (x, y_complex, n)

🔓 Déchiffrement
Le destinataire utilise la clé privée pour recalculer y, puis vérifie :

python
Copier
Modifier
recalculated = (y * n + n^2) % p
Si y_complex == recalculated, le caractère est valide.

💾 Fichiers générés
cles/public_<nom>.json : clé publique

cles/private_<nom>.json : clé privée

📂 Exemple de message chiffré
python
Copier
Modifier
[(72, 34927, 3), (101, 22845, 2), (108, 39211, 7)]
🚀 Menu interactif
Lancement :

bash
Copier
Modifier
python curvax.py
Menu :

markdown
Copier
Modifier
1. Générer une paire de clés
2. Chiffrer un message (complexe)
3. Déchiffrer un message (complexe)
4. Quitter
🧠 Objectif du Projet
Ce projet a été développé dans un but éducatif et expérimental pour explorer différentes techniques de cryptographie :

The Void : stéganographie invisible

Curvax : asymétrie + mathématiques non standards

⚠️ Ces systèmes ne doivent pas être utilisés tels quels pour des données sensibles ou dans des environnements de production.

📚 Prérequis
Python 3.x

Modules standards : random, json, os, math, hashlib

✍️ Auteur
Nicolas Houles
Étudiant en cybersécurité à Guardia Cyber Security School
Passionné de cryptographie, sécurité informatique et projets expérimentaux
