# Exercice Vim 9 — Bash Script / Infra

Ouvre le fichier dans Vim :

```
vim exercices/exercice9/exercice9.txt
```

> **Astuce** : active les numéros de ligne dès l'ouverture :
> `:set number<Entrée>`

---

## Nouvelles commandes de ce niveau

| Commande | Action |
|----------|--------|
| `:set number` | Afficher les numéros de ligne |
| `%` | Sauter au délimiteur correspondant `{` `}` `(` `)` `[` `]` |
| `gd` | Aller à la première occurrence du mot sous le curseur |
| `zz` | Centrer l'écran sur la ligne courante |
| `:g/motif/d` | Rappel — supprimer toutes les lignes contenant un motif |

---

## Modifications à effectuer

### 1. Ligne 1 — Corriger le shebang `bassh` → `bash`
- `/bassh<Entrée>`
- Place-toi sur le second `s` de `bassh`
- Commande : `x`
- Résultat : `#!/bin/bash`

### 2. Ligne 4 — Incrémenter la version `1.0.0` → `2.0.0`
- `/Version<Entrée>`
- Place le curseur sur le `1` de `1.0.0`
- Commande : `Ctrl+A`
- Résultat : `# Version : 2.0.0`

### 3. Ligne 10 — Incrémenter `TIMEOUT=29` → `TIMEOUT=30`
- `/TIMEOUT<Entrée>`
- Place le curseur sur `29`
- Commande : `Ctrl+A`
- Résultat : `TIMEOUT=30`

### 4. Ligne 9 — Incrémenter `MAX_RETRIES=3` → `MAX_RETRIES=5`
- `/MAX_RETRIES<Entrée>`
- Place le curseur sur `3`
- Commande : `2` puis `Ctrl+A`  (incrémenter de 2 d'un coup)
- Résultat : `MAX_RETRIES=5`

### 5. Ligne 14 — Corriger `$APP_NAAME` → `$APP_NAME`
- `/APP_NAAME<Entrée>`
- Place-toi sur le second `A` en trop
- Commande : `x`
- Résultat : `echo "Démarrage du deploiement de $APP_NAME..."`

### 6. Ligne 22 — Corriger `$LOG_FILLE` → `$LOG_FILE`
- `/LOG_FILLE<Entrée>`
- Place-toi sur le `L` en trop (second `L`)
- Commande : `x`
- Résultat : `echo "Fichiers copies avec succes" >> $LOG_FILE`

### 7. Ligne 33 — Corriger `Sleep` → `sleep`
- `/Sleep<Entrée>`
- Place-toi sur le `S` de `Sleep`
- Commande : `~` (basculer la casse d'un caractère)
- Résultat : `sleep 2`

### 8. Ligne 39 — Corriger `stopp` → `stop`
- `/stopp<Entrée>`
- Place-toi sur le `p` en trop
- Commande : `x`
- Résultat : `systemctl stop $APP_NAME`

### 9. Supprimer la ligne de debug
- Commande : `:g/DEBUG/d<Entrée>`
- La ligne `echo "DEBUG: ..."` disparaît.

### 10. Bonus — Utiliser `%` pour naviguer
- Place le curseur sur un `{` de n'importe quelle fonction
- Appuie sur `%` : le curseur saute au `}` correspondant
- Appuie sur `%` encore : il revient au `{`
- (Aucune modification à faire, c'est juste pour explorer)

---

## Sauvegarder et quitter
```
:wq
```

---

## Résultat final attendu

```bash
#!/bin/bash
# Script de déploiement automatique
# Auteur : admin
# Version : 2.0.0

APP_NAME="myapp"
APP_DIR="/opt/myapp"
LOG_FILE="/var/log/myapp.log"
MAX_RETRIES=5
TIMEOUT=30

deploy() {
    echo "Démarrage du deploiement de $APP_NAME..."

    if [ ! -d "$APP_DIR" ]; then
        mkdir -p $APP_DIR
        echo "Repertoire cree : $APP_DIR"
    fi

    cp -r ./dist/* $APP_DIR
    chmod 755 $APP_DIR
    echo "Fichiers copies avec succes" >> $LOG_FILE
}

check_status() {
    local retries=0
    while [ $retries -lt $MAX_RETRIES ]; do
        if systemctl is-active --quiet $APP_NAME; then
            echo "Service $APP_NAME est actif"
            return 0
        fi
        retries=$((retries + 1))
        sleep 2
    done
    echo "ERREUR: Service non disponible apres $MAX_RETRIES tentatives"
    return 1
}

restart_service() {
    systemctl stop $APP_NAME
    systemctl start $APP_NAME
    check_status
}

main() {
    deploy
    restart_service
}

main "$@"
```

---

Une fois terminé, copie dans `soumissions/` et soumets :
```
cp exercices/exercice9/exercice9.txt soumissions/exercice9.txt
```
