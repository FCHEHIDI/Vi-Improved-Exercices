# Exercice Vim 3 — Niveau Intermédiaire

Ouvre le fichier `exercice3.txt` dans Vim :

```
vim exercice3.txt
```

---

## Nouvelles commandes de ce niveau

| Commande | Action |
|----------|--------|
| `dw` | Supprimer le mot sous le curseur (jusqu'au prochain mot) |
| `ciw` | Changer le mot entier sous le curseur (change inner word) |
| `yy` | Copier la ligne courante |
| `dd` + `p` | Couper la ligne et la coller ailleurs |
| `o` | Ouvrir une nouvelle ligne en dessous et passer en insert |
| `n` | Répéter la dernière recherche `/` |
| `:s/ancien/nouveau/` | Remplacer la première occurrence sur la ligne courante |

---

## Modifications à effectuer

### 1. Ligne 3 — Corriger "artificiel" en "artificielle"
- Va à la ligne 3 : `3G`
- Cherche le mot : `/artificiel<Entrée>`
- Place-toi sur le mot `artificiel`
- Commande : `A` pour aller en fin du mot... ou mieux : `A` depuis la fin de la ligne
- Plus simple : utilise `ciw` sur `artificiel` puis tape `artificielle<Echap>`
- Résultat : `Python est utilise en intelligence artificielle.`

### 2. Ligne 5 — Supprimer la ligne entière
- Va à la ligne 5 : `5G`
- Commande : `dd`
- La ligne `SUPPRIMER CETTE LIGNE` disparaît.

### 3. Ligne 6 (maintenant) — Remplacer "Python 2" par "Python 3" (deuxième occurrence seulement)
- La ligne contient : `Il existe deux versions : Python 2 et Python 2.`
- Le second `2` doit devenir `3`
- Commande depuis cette ligne : `:s/Python 2/Python 3/2<Entrée>`
  - Le `2` à la fin indique la 2e occurrence
- Résultat : `Il existe deux versions : Python 2 et Python 3.`

### 4. Lignes 7 et 8 — Il y a une ligne dupliquée, supprimer l'une des deux
- Les lignes 7 et 8 sont identiques : `La communaute Python est tres active.`
- Va à la ligne 7 : `7G`
- Commande : `dd`
- Résultat : il ne reste qu'une seule occurrence.

### 5. Après la dernière ligne — Ajouter une nouvelle ligne
- Va à la dernière ligne : `G`
- Commande : `o` (ouvre une ligne en dessous et passe en mode insertion)
- Tape : `Bonne chance avec Python!`
- Appuie sur `<Echap>`

---

## Sauvegarder et quitter
```
:wq
```

---

## Résultat final attendu

```
Python est un langage de programmation tres populaire.
Il est connu pour sa syntaxe simple et lisible.
Python est utilise en intelligence artificielle.
Python est aussi utilise pour le web et la data.
Il existe deux versions : Python 2 et Python 3.
La communaute Python est tres active.
Pour installer Python, rendez-vous sur python.org.
Bonne chance avec Python!
```

---

Une fois terminé, soumets le contenu de `exercice3.txt` et je vérifie !
