# Exercice Vim 10 — Python / API Monitoring

Ouvre le fichier dans Vim :

```
vim exercices/exercice10/exercice10.txt
```

> Active les numéros de ligne : `:set number<Entrée>`

---

## Nouvelles commandes de ce niveau

| Commande | Action |
|----------|--------|
| `[{` / `]}` | Sauter au `{` ou `}` du bloc courant |
| `=G` | Ré-indenter depuis la ligne courante jusqu'à la fin |
| `dap` | Supprimer un paragraphe entier |
| `vip` | Sélectionner le paragraphe courant |
| `Ctrl+O` | Revenir à la position précédente (historique) |
| `gi` | Retourner au dernier endroit où on était en mode insertion |
| `:%s/motif/nouveau/gc` | Substitution globale avec **confirmation** (`y/n` pour chaque) |

---

## Modifications à effectuer

### 1. Corriger l'import `reqests` → `requests` (3 occurrences)
- Il y a `reqests` à 4 endroits dans le fichier.
- Commande : `:%s/reqests/requests/g<Entrée>`

### 2. Ligne 6 — Corriger `Dictt` → `Dict`
- `/Dictt<Entrée>`
- Place-toi sur le `t` en trop
- Commande : `x`
- Résultat : `from typing import List, Dict`

### 3. Ligne 29 — Corriger `TIMEOOUT` → `TIMEOUT`
- `/TIMEOOUT<Entrée>`
- Place-toi sur le `O` en trop
- Commande : `x`
- Résultat : `response = self.session.get(url, timeout=TIMEOUT)`

### 4. Ligne 23 — Corriger `Content-type` → `Content-Type`
- `/Content-type<Entrée>`
- Place le curseur sur le `t` de `type`
- Commande : `~`
- Résultat : `"Content-Type": "application/json"`

### 5. Ligne 52 — Corriger `false` → `False` (Python sensible à la casse !)
- `/false<Entrée>`
- Place le curseur sur le `f`
- Commande : `~`
- Résultat : `return False`

### 6. Ligne 64 — Corriger `APIclient` → `APIClient`
- `/APIclient<Entrée>`
- Place le curseur sur le `c` de `client`
- Commande : `~`
- Résultat : `def check_all_services(client: APIClient, services: List[str]) -> None:`

### 7. Ligne 42 — Supprimer l'espace avant `:` dans `message : str`
- `/message :<Entrée>`
- Place le curseur sur l'espace avant `:`
- Commande : `x`
- Résultat : `def post_alert(self, service: str, level: str, message: str) -> bool:`

### 8. Substitution avec confirmation — uniformiser `ERREUR:` en `ERROR:`
- Commande : `:%s/ERREUR:/ERROR:/gc<Entrée>`
- Vim te demandera confirmation pour chaque occurrence
- Réponds `y` pour accepter, `n` pour refuser
- Accepte toutes les occurrences.

---

## Sauvegarder et quitter
```
:wq
```

---

## Résultat final attendu (lignes clés)

```python
import requests
from typing import List, Dict

...
        self.session  = requests.Session()
        self.session.headers.update({
            "Authorization": f"Bearer {self.api_key}",
            "Content-Type": "application/json"
        })

    def get_metrics(self, service: str) -> Dict:
        ...
            response = self.session.get(url, timeout=TIMEOUT)
        except requests.exceptions.Timeout:
            print(f"ERROR: Timeout apres {TIMEOUT}s pour {service}")
        except requests.exceptions.HTTPError as e:
            print(f"ERROR HTTP: {e}")

    def post_alert(self, service: str, level: str, message: str) -> bool:
        ...
            print(f"ERROR: Impossible d envoyer l alerte : {e}")
            return False

def check_all_services(client: APIClient, services: List[str]) -> None:
```

---

Une fois terminé, copie dans `soumissions/` et soumets :
```
cp exercices/exercice10/exercice10.txt soumissions/exercice10.txt
```
