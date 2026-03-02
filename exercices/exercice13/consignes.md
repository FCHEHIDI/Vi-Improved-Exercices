# Exercice Vim 13 — Dockerfile DevSecOps

Ouvre le fichier dans Vim :

```
vim exercices/exercice13/exercice13.txt
```

---

## Contexte DevSecOps

Ce Dockerfile contient des problèmes de sécurité classiques en plus des fautes de frappe. Un bon DevSecOps les repère et les corrige avant le build.

---

## Nouvelles commandes

| Commande | Action |
|----------|--------|
| `O` | Ouvrir une ligne **au-dessus** du curseur et passer en insertion |
| `yyp` | Dupliquer la ligne courante (copier + coller en dessous) |
| `dG` | Supprimer de la ligne courante jusqu'à la fin du fichier |
| `d}` | Supprimer jusqu'à la prochaine ligne vide |
| `:g/^$/d` | Supprimer toutes les lignes vides |

---

## Modifications à effectuer

### 1. Ligne 2 — Fixer l'image de base (pas de tag = danger !)
- `FROM python:3.9` doit devenir `FROM python:3.9-slim`
- `/^FROM<Entrée>` → `A-slim<Echap>` (`A` = insérer en fin de ligne)

### 2. Ligne 14 — Corriger `devellopment` → `production` (on est en prod !)
- `/devellopment<Entrée>` → `ciw` → tape `production<Echap>`

### 3. Lignes 15-16 — Supprimer les secrets en clair (faille de sécurité !)
- Les lignes `ENV SECRET_KEY=...` et `ENV DB_PASSWORD=...` ne doivent JAMAIS être dans un Dockerfile.
- Va sur la ligne `ENV SECRET_KEY` : `/ENV SECRET_KEY<Entrée>`
- Supprime les 2 lignes : `2dd`

### 4. Ligne 20 — Corriger `--timeout=10` → `--timeout=10s` (unité manquante)
- `/timeout=10<Entrée>` → place-toi après `10` → `a s<Echap>` (`a` = insérer après le curseur)

### 5. Ligne 24 — Corriger `rune` → `run`
- `/rune<Entrée>` → place-toi sur le `e` final → `x`

### 6. Ajouter un utilisateur non-root avant le CMD (bonne pratique sécurité)
- Va sur la ligne du `CMD` : `G`
- Ouvre une ligne au-dessus : `O`
- Tape : `USER 1001`
- `<Echap>`

---

## Résultat final attendu

```dockerfile
FROM python:3.9-slim

WORKDIR /app

COPY requirements.txt requirements.txt
RUN pip install -r requirements.txt

COPY . .

ENV FLASK_APP=app.py
ENV FLASK_ENV=production

EXPOSE 5000

HEALTHCHECK --interval=30s --timeout=10s --retries=3 \
  CMD curl -f http://localhost:5000/health || exit 1

USER 1001
CMD ["python", "-m", "flask", "run"]
```

---

```
cp exercices/exercice13/exercice13.txt soumissions/exercice13.txt
```
