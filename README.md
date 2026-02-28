# Vi Improved — Exercices

![Editing with Vim](assets/EditantVim.png)

Entraîne-toi à utiliser Vim avec des exercices progressifs, du niveau débutant au niveau avancé.

## Structure du dépôt

```
.
├── exercices/
│   ├── exercice1/
│   │   ├── consignes.md   ← instructions pas à pas
│   │   └── exercice1.txt  ← fichier à modifier
│   ├── exercice2/
│   ├── exercice3/
│   ├── exercice4/
│   ├── exercice5/
│   ├── exercice6/
│   └── exercice7/
└── soumissions/           ← fichiers complétés pour évaluation
```

## Comment utiliser ce dépôt

1. Lis le fichier `consignes.md` de l'exercice choisi.
2. Ouvre le fichier `.txt` correspondant dans Vim :
   ```
   vim exercices/exerciceN/exerciceN.txt
   ```
3. Applique les modifications demandées dans les consignes.
4. Sauvegarde ton fichier complété dans `soumissions/`.

## Progression des exercices

| Exercice | Niveau | Commandes clés |
|----------|--------|----------------|
| 1 | Débutant | `~`, `A`, `i`, `dd` |
| 2 | Débutant+ | `cw`, `x`, `r`, `w`, `b` |
| 3 | Intermédiaire | `ciw`, `yy`, `dd`+`p`, `o`, `:s/x/y/` |
| 4 | Intermédiaire+ | `dd`+`p`, `:%s/x/y/g`, `f<c>` |
| 5 | Avancé | `V`+`<`, `Ndd`, `:%s/\b..\b/`, mode visuel |
| 6 | Avancé+ | macros `qa`/`@a`, `Ctrl+V`, `ci"`, `ci(`, `J` |
| 7 | Expert | `Ctrl+A`/`Ctrl+X`, `gUU`/`guu`, `gU$`, `dt<c>` |

## Auteur

[FCHEHIDI](https://github.com/FCHEHIDI)
