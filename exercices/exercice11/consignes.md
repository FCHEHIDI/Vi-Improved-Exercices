# Exercice Vim 11 — CI/CD GitHub Actions

Ouvre le fichier dans Vim :

```
vim exercices/exercice11/exercice11.txt
```

> Active les numéros de ligne : `:set number<Entrée>`

---

## Contexte

Tu viens de récupérer un fichier de pipeline GitHub Actions écrit à la va-vite. Il contient des fautes de frappe, des erreurs de casse et des incohérences qui empêcheraient le pipeline de tourner. Ton job : le corriger.

---

## Nouvelles commandes de ce niveau

| Commande | Action |
|----------|--------|
| `:set ignorecase` | Rendre les recherches insensibles à la casse |
| `:set noignorecase` | Réactiver la sensibilité à la casse |
| `gf` | Ouvrir le fichier dont le nom est sous le curseur |
| `Ctrl+W v` | Diviser la fenêtre verticalement |
| `Ctrl+W q` | Fermer la fenêtre courante |
| `:earlier 1m` | Revenir à l'état du fichier il y a 1 minute |
| `:later 1m` | Avancer dans l'historique |

---

## Modifications à effectuer

### 1. Ligne 4 — Corriger `pussh` → `push`
- `/pussh<Entrée>` puis `x`

### 2. Ligne 6 — Corriger `Main` → `main` (la casse compte en YAML/Git !)
- `/pull_request<Entrée>` pour aller sur la bonne ligne
- Place-toi sur le `M` de `Main`
- `~`

### 3. Ligne 14 — Corriger `Jobs` → `jobs`
- `/^Jobs<Entrée>`
- Place-toi sur le `J`
- `~`

### 4. Ligne 16 — Supprimer la ligne `步驟:` (caractères parasites)
- `/步驟<Entrée>`
- `dd`

### 5. Ligne 20 — Corriger `set up` → `Set up` (convention GitHub Actions)
- `/set up Python<Entrée>`
- Place-toi sur le `s` de `set`
- `~`

### 6. Ligne 27 — Corriger `dependancies` → `dependencies`
- `/dependancies<Entrée>`
- `ciw` puis tape `dependencies<Echap>`

### 7. Ligne 29 — Corriger `coverge` → `coverage`
- `/coverge<Entrée>`
- `ciw` puis tape `coverage<Echap>`

### 8. Ligne 33 — Remplacer `True` → `true` (YAML : booléens en minuscules)
- `/fail_ci_if_error<Entrée>`
- Place-toi sur `True`
- `ciw` puis tape `true<Echap>`

### 9. Ligne 36 — Corriger `needs: tests` → `needs: test`
- `/needs: tests<Entrée>`
- Place-toi sur le `s` final de `tests`
- `x`

### 10. Ligne 42 — Corriger `build Docker` → `Build Docker` (convention)
- `/build Docker<Entrée>`
- `~` sur le `b`

### 11. Ligne 52 — Corriger `deploy to` → `Deploy to` (convention)
- `/deploy to production<Entrée>`
- `~` sur le `d`

### 12. Ligne 50 — Corriger `refs/heads/Main` → `refs/heads/main`
- `/refs\/heads\/Main<Entrée>`
- Place-toi sur le `M`
- `~`

### 13. Ligne 57 — Corriger `SSH_PRIVAT_KEY` → `SSH_PRIVATE_KEY`
- `/PRIVAT<Entrée>`
- `ciw` puis tape `SSH_PRIVATE_KEY<Echap>`

### 14. Ligne 61 — Remplacer `True` → `true`
- `/docker stop myapp || True<Entrée>`
- Place-toi sur `True`
- `ciw` puis tape `true<Echap>`

---

## Sauvegarder et quitter
```
:wq
```

---

## Résultat final attendu (lignes clés)

```yaml
name: CI/CD Pipeline

on:
  push:
    branches: [main, develop]
  pull_request:
    branches: [main]

env:
  ...

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
    - name: Checkout code
      uses: actions/checkout@v2

    - name: Set up Python
      ...

    - name: Install dependencies
      run: |
        pip install -r requirements.txt
        pip install pytest coverage

    - name: Run tests
      ...
      with:
        ...
        fail_ci_if_error: true

  build:
    needs: test
    ...
    - name: Build Docker image
    ...

  deploy:
    needs: build
    ...
    if: github.ref == "refs/heads/main"
    steps:
    - name: Deploy to production
      with:
        ...
        key: ${{ secrets.SSH_PRIVATE_KEY }}
        script: |
          ...
          docker stop myapp || true
```

---

Une fois terminé, copie dans `soumissions/` et soumets :
```
cp exercices/exercice11/exercice11.txt soumissions/exercice11.txt
```
