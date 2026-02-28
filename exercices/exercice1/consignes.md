# Exercice Vim 1 — Niveau Débutant

Ouvre le fichier `exercice1.txt` dans Vim :

```
vim exercice1.txt
```

---

## Modifications à effectuer

### 1. Ligne 1 — Capitaliser "bonjour"
- Place le curseur sur le `b` de `bonjour` (au début du fichier)
- Commande : `~`
- Résultat attendu : `Bonjour le monde`

### 2. Ligne 1 — Ajouter `!` à la fin
- Reste sur la ligne 1
- Commande : `A!<Echap>`  (`A` = insérer en fin de ligne)
- Résultat attendu : `Bonjour le monde!`

### 3. Ligne 2 — Corriger "tain" en "train"
- Cherche le mot avec : `/tain<Entrée>`
- Place-toi sur le `t` de `tain`
- Commande : `i` puis tape `r` puis `<Echap>`
- (ou plus rapide : `r` n'insère qu'un seul caractère — ici il faut en insérer un, donc `i` est adapté)
- Résultat attendu : `Je suis en train d'apprendre Vim.`

### 4. Ligne 4 — Capitaliser "vim" en "Vim"
- Va à la ligne 4 : `4G`
- Place-toi sur le `v` de `vim` (début de ligne, touche `0` puis `w` si nécessaire)
- Commande : `~`
- Résultat attendu : `Vim est disponible sur tous les systemes.`

### 5. Ligne 5 — Supprimer toute la ligne
- Va à la ligne 5 : `5G`
- Commande : `dd`
- La ligne `Cette ligne doit etre supprimee.` doit disparaître.

---

## Sauvegarder et quitter
```
:wq
```

---

## Résultat final attendu

```
Bonjour le monde!
Je suis en train d'apprendre Vim.
C'est un editeur tres puissant.
Vim est disponible sur tous les systemes.
Bonne continuation!
```

---

Une fois terminé, soumets le contenu de ton fichier `exercice1.txt` et je vérifie si tout est bon !
