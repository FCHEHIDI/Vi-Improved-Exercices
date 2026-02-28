# Exercice Vim 8 — Niveau Expert

Ouvre le fichier `exercice8.txt` dans Vim :

```
vim exercices/exercice8/exercice8.txt
```

---

## Nouvelles commandes de ce niveau

| Commande | Action |
|----------|--------|
| `:g/motif/d` | Supprimer toutes les lignes contenant `motif` |
| `:sort` | Trier les lignes sélectionnées alphabétiquement |
| `D` | Supprimer du curseur jusqu'à la fin de la ligne |
| `C` | Changer du curseur jusqu'à la fin de la ligne |
| `*` | Chercher le mot sous le curseur (occurrences suivantes) |
| `n` / `N` | Occurrence suivante / précédente |
| `:.,$s/motif/nouveau/g` | Substitution de la ligne courante jusqu'à la fin du fichier |

---

## Modifications à effectuer

### 1. Supprimer toutes les lignes `# A SUPPRIMER` en une seule commande
- Il y a 3 lignes `# A SUPPRIMER` dispersées dans le fichier.
- Commande : `:g/# A SUPPRIMER/d<Entrée>`
- Les 3 lignes disparaissent d'un coup.

### 2. Trier la liste de courses (lignes 3 à 13 après suppression)
- La liste `pain`, `lait`, `oeufs`... doit être triée alphabétiqueument.
- Sélectionne les lignes avec `V` puis les 10 éléments de la liste.
- Commande : `:sort<Entrée>` (s'applique à la sélection visuelle)
- Résultat : la liste est triée de A à Z.

### 3. Ligne "courses urgentes" — Corriger `aujourd hui` en `aujourd'hui`
- Cherche : `/aujourd<Entrée>`
- Place-toi sur l'espace entre `aujourd` et `hui`
- Commande : `r'`
- Résultat : `## courses urgentes (a faire aujourd'hui)`

### 4. Ligne "jus d orange" — Corriger en `jus d'orange`
- Cherche : `/d o<Entrée>`
- Place-toi sur l'espace entre `d` et `orange`
- Commande : `r'`
- Résultat : `jus d'orange`

### 5. Trier les lignes du budget (les lignes `article : prix`)
- Les lignes de budget doivent aussi être triées alphabétiquement pour correspondre à la liste triée.
- Sélectionne visuellement toutes les lignes `article : prix` avec `V`
- Commande : `:sort<Entrée>`

### 6. Dernière ligne — Remplacer `0.00` par le vrai total `23.10`
- Va sur la dernière ligne : `G`
- Place le curseur sur `0.00`
- Commande : `C` puis tape `23.10<Echap>`
  - `C` supprime du curseur jusqu'à la fin de ligne et passe en insertion
- Résultat : `total prevu : 23.10`

---

## Sauvegarder et quitter
```
:wq
```

---

## Résultat final attendu

```
## liste de courses

bananes
beurre
carottes
courgettes
fromage
lait
oeufs
pain
pommes
yaourt

## courses urgentes (a faire aujourd'hui)

café
jus d'orange
sucre

## budget estimé

bananes : 1.80
beurre : 1.70
carottes : 1.20
courgettes : 1.40
fromage : 3.20
lait : 0.90
oeufs : 2.80
pain : 1.50
pommes : 2.50
yaourt : 2.10

total prevu : 23.10
```

---

Une fois terminé, copie dans `soumissions/` et soumets :
```
cp exercices/exercice8/exercice8.txt soumissions/exercice8.txt
```
