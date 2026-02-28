# Vi Improved — Exercices

<div align="center">
<table>
  <tr>
    <td><img src="assets/eteVim.png" width="250"/></td>
    <td><img src="assets/EditantVim.png" width="250"/></td>
  </tr>
  <tr>
    <td><img src="assets/enhiverVim.png" width="250"/></td>
    <td><img src="assets/printempsVim.png" width="250"/></td>
  </tr>
</table>
</div>

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
│   ├── exercice7/
│   ├── exercice8/
│   ├── exercice9/
│   ├── exercice10/
│   └── exercice11/
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
| 8 | Expert+ | `:g/motif/d`, `:sort`, `D`, `C`, `*` |
| 9 | Infra/Bash | `%`, `gd`, `zz`, `:set number`, `N Ctrl+A` |
| 10 | Python/API | `:%s/x/y/gc`, `gi`, `Ctrl+O`, `vip`, `dap` |
| 11 | CI/CD YAML | `:set ignorecase`, `Ctrl+W v`, `:earlier`, `gf` |

## Auteur

[FCHEHIDI](https://github.com/FCHEHIDI)
