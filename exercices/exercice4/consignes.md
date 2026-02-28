# Exercice Vim 4 — Niveau Intermédiaire+

Ouvre le fichier `exercice4.txt` dans Vim :

```
vim exercice4.txt
```

---

## Nouvelles commandes de ce niveau

| Commande | Action |
|----------|--------|
| `dd` + `p` | Couper une ligne et la coller en dessous de la position courante |
| `:%s/ancien/nouveau/g` | Remplacer **toutes** les occurrences dans tout le fichier |
| `f<c>` | Aller au prochain caractère `<c>` sur la ligne courante |
| `;` | Répéter le dernier `f` vers l'avant |

---

## Modifications à effectuer

### 1. Ligne 1 — Corriger "langaje" en "langage"
- `/langaje<Entrée>` pour chercher le mot
- `ciw` puis tape `langage<Echap>`
- Résultat : `JavaScript est un langage de programmation populaire.`

### 2. Ligne 4 — Supprimer la ligne
- `4G` puis `dd`
- La ligne `--- SUPPRIMER CETTE LIGNE ---` disparaît.

### 3. Ligne 4 (après suppression) — Corriger "d executer" en "d'executer"
- `/d e<Entrée>` pour trouver l'espace fautif
- Place-toi sur l'espace entre `d` et `e`
- `r'` pour remplacer l'espace par une apostrophe
- Résultat : `Node.js permet d'executer JavaScript cote serveur.`

### 4. Ligne 5 (après suppression) — Corriger "c est" en "c'est"
- `/c est<Entrée>` pour trouver la faute
- Place-toi sur l'espace entre `c` et `est`
- `r'`
- Résultat : `Apprenez JavaScript, c'est un excellent choix.`

### 5. Lignes 5 et 6 — Inverser les deux lignes
- La ligne `Apprenez...` (ligne 5) doit passer APRES `Les frameworks...` (ligne 6)
- `5G` pour aller à la ligne 5
- `dd` pour couper `Apprenez...`
- Le curseur est maintenant sur `Les frameworks...`
- `p` pour coller en dessous
- Résultat :
  ```
  Les frameworks populaires sont React, Vue et Angular.
  Apprenez JavaScript, c'est un excellent choix.
  ```

### 6. Dernière ligne — Corriger "dynamyque" en "dynamique"
- `G` pour aller à la dernière ligne
- `/dynamyque<Entrée>`
- `ciw` puis tape `dynamique<Echap>`
- Résultat : `JavaScript est un langage au typage dynamique.`

### 7. Tout le fichier — Remplacer "JavaScript" par "JS" partout
- Commande (depuis n'importe où) : `:%s/JavaScript/JS/g<Entrée>`
- Toutes les occurrences de `JavaScript` dans le fichier deviennent `JS`.

---

## Sauvegarder et quitter
```
:wq
```

---

## Résultat final attendu

```
JS est un langage de programmation populaire.
Il est utilise pour le web, les applications et les serveurs.
Il a ete cree par Brendan Eich en 1995.
Node.js permet d'executer JS cote serveur.
Les frameworks populaires sont React, Vue et Angular.
Apprenez JS, c'est un excellent choix.
JS est un langage au typage dynamique.
```

---

Une fois terminé, soumets le contenu de `exercice4.txt` et je vérifie !
