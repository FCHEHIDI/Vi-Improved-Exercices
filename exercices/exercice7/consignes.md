# Exercice Vim 7 — Niveau Expert

Ouvre le fichier `exercice7.txt` dans Vim :

```
vim exercices/exercice7/exercice7.txt
```

---

## Nouvelles commandes de ce niveau

| Commande | Action |
|----------|--------|
| `Ctrl+A` | Incrémenter le nombre sous le curseur |
| `Ctrl+X` | Décrémenter le nombre sous le curseur |
| `gUU` | Mettre toute la ligne en MAJUSCULES |
| `guu` | Mettre toute la ligne en minuscules |
| `gU<mouvement>` | Mettre en majuscules jusqu'au mouvement (ex: `gUw`) |
| `gu<mouvement>` | Mettre en minuscules jusqu'au mouvement (ex: `guw`) |
| `dt<c>` | Supprimer jusqu'au caractère `<c>` (sans l'inclure) |
| `"ay{mouvement}` | Copier dans le registre nommé `a` |
| `"ap` | Coller depuis le registre `a` |

---

## Modifications à effectuer

### 1. Ligne 1 — Mettre le titre en majuscules
- Va à la ligne 1 : `1G`
- La ligne est `## configuration du serveur`
- Commande : `gUU`
- Résultat : `## CONFIGURATION DU SERVEUR`

### 2. Ligne 4 — Corriger le port 8079 → 8080
- Va sur la ligne `port = 8079`
- Place le curseur sur `8079`
- Appuie sur `Ctrl+A` une fois pour incrémenter
- Résultat : `port = 8080`

### 3. Ligne 5 — Mettre `TRUE` en minuscules
- Va sur la ligne `debug = TRUE`
- Place le curseur n'importe où sur `TRUE`
- Commande : `guw` (minuscules sur un mot)
- Résultat : `debug = true`

### 4. Ligne 6 — Incrémenter max_connections de 99 à 100
- Va sur la ligne `max_connections = 99`
- Place le curseur sur `99`
- Commande : `Ctrl+A`
- Résultat : `max_connections = 100`

### 5. Ligne 7 — Incrémenter timeout de 29 à 30
- Va sur la ligne `timeout = 29`
- Place le curseur sur `29`
- Commande : `Ctrl+A`
- Résultat : `timeout = 30`

### 6. Ligne 16 — Mettre les permissions `moderateur` en majuscules
- La ligne `moderateur: lire ecrire` doit avoir ses permissions en majuscules.
- Va sur cette ligne, place le curseur sur `lire`
- Commande : `gUU` va tout mettre en majuscules — trop radical.
- Utilise plutôt `gU$` (majuscules du curseur jusqu'à la fin de ligne)
- Place-toi sur le `l` de `lire`
- Commande : `gU$`
- Résultat : `moderateur: LIRE ECRIRE`

### 7. Ligne 20 — Mettre `log_level` en minuscules
- La ligne est `log_level = "info"` — c'est déjà correct, rien à faire ici.

### 7. Ligne 22 — Mettre `log_rotation` en minuscules
- La ligne est `log_rotation = TRUE`
- Place le curseur sur `TRUE`
- Commande : `guw`
- Résultat : `log_rotation = true`

### 8. Ligne 23 — Incrémenter max_log_size de 4 à 5
- Va sur la ligne `max_log_size = 4`
- Place le curseur sur `4`
- Commande : `Ctrl+A`
- Résultat : `max_log_size = 5`

---

## Sauvegarder et quitter
```
:wq
```

---

## Résultat final attendu

```
## CONFIGURATION DU SERVEUR

host = "localhost"
port = 8080
debug = true
max_connections = 100
timeout = 30

## liste des utilisateurs autorisés

admin
moderateur
utilisateur

## permissions par role

admin: LIRE ECRIRE SUPPRIMER
moderateur: LIRE ECRIRE
utilisateur: LIRE

## journalisation

log_level = "info"
log_file = "/var/log/app.log"
log_rotation = true
max_log_size = 5
```

---

Une fois terminé, copie le fichier dans `soumissions/` et soumets :
```
cp exercices/exercice7/exercice7.txt soumissions/exercice7.txt
```
