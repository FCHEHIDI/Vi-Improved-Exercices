# Exercice Vim 6 — Niveau Avancé

Ouvre le fichier `exercice6.txt` dans Vim :

```
vim exercices/exercice6/exercice6.txt
```

---

## Nouvelles commandes de ce niveau

| Commande | Action |
|----------|--------|
| `qa` ... `q` | Enregistrer une macro dans le registre `a` |
| `@a` | Rejouer la macro `a` |
| `3@a` | Rejouer la macro `a` 3 fois |
| `Ctrl+Q` (Windows) / `Ctrl+V` (Linux) | Mode visuel par bloc (sélection rectangulaire) |
| `I` (en mode visuel bloc) | Insérer au début de chaque ligne sélectionnée |
| `:3,10norm I  ` | Alternative Windows : indenter les lignes 3 à 10 via `:norm` |
| `J` | Fusionner la ligne courante avec la suivante |
| `ci"` | Changer le contenu entre guillemets |
| `ci(` | Changer le contenu entre parenthèses |

---

## Modifications à effectuer

### 1. Lignes 3 à 8 — Capitaliser "java", "rust" et "go" (3 mots à corriger)
- Les lignes `3 - java`, `5 - rust` et `7 - go` ont leur langage en minuscule.
- Utilise une macro pour automatiser :
  - Va sur le `j` de `java` : `/java<Entrée>`
  - Enregistre la macro : `qa` puis tape `~` puis `q`
  - Cherche `rust` : `/rust<Entrée>` puis rejoue : `@a`
  - Cherche `go` : `/go<Entrée>` puis rejoue : `@a`
- Résultat : `3 - Java`, `5 - Rust`, `7 - Go`

### 2. Ligne 13 — Changer le contenu entre guillemets pour Java
- La ligne `Java : "un langage oriente objet tres utilise en entreprise"` a le mauvais contenu (c'est la description de Java qui est entre parenthèses en ligne 14).
- Place-toi n'importe où sur les guillemets de la ligne 13 (`Java :`)
  - Attends... la ligne 13 contient `Python`. Place-toi sur la ligne `Java : (...)`.
- Sur la ligne `Java : (langage oriente objet tres utilise en entreprise)` :
  - Place le curseur entre les parenthèses
  - Commande : `ci(` puis tape `langage oriente objet tres utilise en entreprise` puis `<Echap>`
  - La ligne ne change pas — mais entraîne-toi au mouvement `ci(`

### 2. (reformulé) Ligne 12 — Corriger la description de Python
- La ligne est : `Python : "un langage polyvalent et facile a prendre en main"`
- Elle est correcte, mais utilise `ci"` pour la remplacer par :
  `langage polyvalent et facile a apprendre`
- Place le curseur n'importe où dans les guillemets
- Commande : `ci"` puis tape `langage polyvalent et facile a apprendre` puis `<Echap>`
- Résultat : `Python : "langage polyvalent et facile a apprendre"`

### 3. Lignes 17 et 18 — Fusionner les deux lignes en une seule
- La ligne `Note importante :` et la ligne `Cette note est en trop.` doivent devenir une seule puis être supprimées.
- Va à la ligne 17 : `17G`
- Fusionne avec la suivante : `J`
- Résultat : `Note importante : Cette note est en trop.`
- Puis supprime la ligne fusionnée : `dd`

### 4. Lignes 3 à 10 — Indenter la liste de 2 espaces via un bloc visuel

> ⚠️ **Windows** : `Ctrl+V` est souvent capturé par le terminal pour coller.
> Utilise `Ctrl+Q` à la place pour entrer en mode visuel bloc.

**Méthode A — visuel bloc (Linux/Mac ou terminal compatible) :**
- Va à la ligne 3 : `3G`
- Mode visuel bloc : `Ctrl+Q` (Windows) ou `Ctrl+V` (Linux/Mac)
- Sélectionne jusqu'à la ligne 10 : `7j`
- Insère au début de chaque ligne : `I` puis tape `  ` (2 espaces) puis `<Echap>`
- Note : l'indentation n'apparaît que sur la première ligne pendant la frappe, elle s'applique à toutes après `<Echap>`.

**Méthode B — commande `:norm` (fonctionne partout) :**
- Commande : `:3,10norm I  <Entrée>`
  - `:3,10` = appliquer sur les lignes 3 à 10
  - `norm I  ` = exécuter la commande normale `I` suivi de 2 espaces
- Résultat identique, sans passer par le mode visuel bloc.

- Résultat : chaque ligne de la liste est indentée de 2 espaces.

---

## Sauvegarder et quitter
```
:wq
```

---

## Résultat final attendu

```
Les langages de programmation les plus populaires :

  1 - Python
  2 - JavaScript
  3 - Java
  4 - C++
  5 - Rust
  6 - TypeScript
  7 - Go
  8 - Kotlin

Description de chaque langage :

Python : "langage polyvalent et facile a apprendre"
JavaScript : "le langage du web par excellence"
Java : (langage oriente objet tres utilise en entreprise)
C++ : (langage de bas niveau, tres performant)
Rust : (langage systeme moderne avec gestion memoire sure)

Les contributions sont les bienvenues.
```

---

Une fois terminé, copie le fichier dans `soumissions/exercice6.txt` et soumets !

```
cp exercices/exercice6/exercice6.txt soumissions/exercice6.txt
```
