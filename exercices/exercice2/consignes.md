# Exercice Vim 2 — Niveau Débutant+

Ouvre le fichier `exercice2.txt` dans Vim :

```
vim exercice2.txt
```

---

## Nouvelles commandes de ce niveau

| Commande | Action |
|----------|--------|
| `cw` | Changer le mot sous le curseur (et passer en mode insertion) |
| `x` | Supprimer le caractère sous le curseur |
| `r<c>` | Remplacer le caractère sous le curseur par `<c>` (sans passer en insert) |
| `w` | Avancer d'un mot |
| `b` | Reculer d'un mot |

---

## Modifications à effectuer

### 1. Ligne 1 — Remplacer "outil" par "editeur"
- Va à la ligne 1 : `gg` (ou `1G`)
- Avance jusqu'au mot `outil` : tape `w` plusieurs fois (ou `/outil<Entrée>`)
- Commande : `cw` puis tape `editeur` puis `<Echap>`
- Résultat : `Vim est un editeur de textte tres populaire.`

### 2. Ligne 1 — Supprimer le "t" en trop dans "textte"
- Cherche le mot : `/textte<Entrée>`
- Place-toi sur le second `t` (le `t` en trop, 4e caractère du mot)
- Commande : `x`
- Résultat : `Vim est un editeur de texte tres populaire.`

### 3. Ligne 5 — Supprimer la ligne entière
- Va à la ligne 5 : `5G`
- Commande : `dd`
- La ligne `CETTE LIGNE EST EN TROP` disparaît.

### 4. Ligne 7 → maintenant ligne 6 — Corriger "d ecrire" en "d'ecrire"
- Cherche l'espace fautif : `/d e<Entrée>`
- Place-toi exactement sur l'espace entre `d` et `e`
- Commande : `r'`  (remplace l'espace par une apostrophe, sans quitter le mode normal)
- Résultat : `Le mode insertion permet d'ecrire du texte.`

---

## Sauvegarder et quitter
```
:wq
```

---

## Résultat final attendu

```
Vim est un editeur de texte tres populaire.
Il a ete cree par Bram Moolenaar en 1991.
Vim signifie "Vi IMproved".
On peut naviguer sans utiliser la souris.
Le mode normal est le mode par defaut.
Le mode insertion permet d'ecrire du texte.
Pour quitter vim on tape :q!.
```

---

Une fois terminé, soumets le contenu de `exercice2.txt` et je vérifie !
