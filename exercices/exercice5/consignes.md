# Exercice Vim 5 — Niveau Avancé

Ouvre le fichier `exercice5.txt` dans Vim :

```
vim exercice5.txt
```

---

## Nouvelles commandes de ce niveau

| Commande | Action |
|----------|--------|
| `V` | Passer en mode visuel ligne (sélectionner des lignes entières) |
| `d` (en mode visuel) | Supprimer la sélection |
| `<` / `>` (en mode visuel) | Désindenter / indenter la sélection |
| `3dd` | Supprimer 3 lignes d'un coup |
| `ma` | Poser un marqueur nommé `a` sur la ligne courante |
| `` `a `` | Sauter au marqueur `a` |
| `:g/motif/d` | Supprimer toutes les lignes contenant un motif |

---

## Modifications à effectuer

### 1. Lignes 2 et 3 — Capitaliser "git" en "Git" partout dans le fichier
- Commande : `:%s/\bgit\b/Git/g<Entrée>`
  - `\b` = délimiteur de mot (évite de remplacer `github` par `Githubub`)
- Résultat : toutes les occurrences de `git` seul deviennent `Git`.

### 2. Ligne 5 — Supprimer la ligne `--- A SUPPRIMER ---`
- `5G` puis `dd`

### 3. Lignes 8, 9 et 10 (après suppression) — Désindenter 3 lignes
- Ces lignes commencent par 4 espaces et ne devraient pas être indentées.
- `8G` pour aller à la ligne 8
- Passe en mode visuel ligne : `V`
- Sélectionne jusqu'à la ligne 10 : `2j`
- Désindente : `<` (une fois)
- Résultat : les 3 lignes perdent leur indentation.

### 4. Lignes 13, 14 et 15 — Supprimer les doublons en une seule commande
- Il y a 3 lignes identiques `Git est indispensable pour le travail en equipe.`
- Va à la ligne 13 : `13G`
- Supprime 2 lignes d'un coup (il faut garder une) : `2dd`

### 5. Dernière ligne — Ajouter deux nouvelles lignes
- `G` pour aller à la dernière ligne
- `o` pour ouvrir une ligne en dessous
- Tape : `N oubliez pas de consulter la documentation.`
- `<Echap>` puis `o` à nouveau
- Tape : `Bonne pratique : committez souvent!`
- `<Echap>`

---

## Sauvegarder et quitter
```
:wq
```

---

## Résultat final attendu

```
Git est un logiciel de gestion de versions.
Git a ete cree par Linus Torvalds en 2005.
Git est un logiciel libre et open source.
Il est utilise par des millions de developpeurs.
Les commandes de base sont les suivantes :
Git init initialise un depot.
Git clone copie un depot distant.
Git add ajoute des fichiers a l index.
Git commit enregistre les modifications.
Git push envoie les commits vers le serveur.
Git pull recupere les commits du serveur.
Git est indispensable pour le travail en equipe.
N oubliez pas de consulter la documentation.
Bonne pratique : committez souvent!
```

---

Une fois terminé, soumets le contenu de `exercice5.txt` et je vérifie !
