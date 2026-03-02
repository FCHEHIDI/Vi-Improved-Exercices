# Exercice Vim 14 — Tests Automatisés (pytest)

Ouvre le fichier dans Vim :

```
vim exercices/exercice14/exercice14.txt
```

---

## Contexte

Fichier de tests pytest avec des erreurs diverses : mauvais noms de méthodes, erreurs de casse Python, fautes de frappe. Certaines sont subtiles !

---

## Nouvelles commandes

| Commande | Action |
|----------|--------|
| `]m` | Sauter à la prochaine définition de méthode/fonction |
| `[m` | Sauter à la définition précédente |
| `zc` | Fermer un fold (replier un bloc) |
| `zo` | Ouvrir un fold |
| `n` + `.` | Chercher occurrence suivante et répéter la dernière action |

---

## Modifications à effectuer

### 1. `setup_methode` → `setup_method` (pytest ne reconnaîtra pas la méthode !)
- `/setup_methode<Entrée>` → `ciw` → tape `setup_method<Echap>`

### 2. `test_addition_negatif` → `test_addition_negative` (convention anglaise)
- `/negatif<Entrée>` → `ciw` → tape `negative<Echap>`

### 3. `substract` → `subtract`
- `/substract<Entrée>` → `ciw` → tape `subtract<Echap>`

### 4. `self.calc.power(2, 8)` → résultat attendu est `256`, mais `2^8 = 256` ✅ — par contre la valeur doit être `256`, vérifier... c'est bon.

### 5. `With pytest.raises` → `with pytest.raises` (Python : `with` en minuscule !)
- `/With pytest<Entrée>` → `~` sur le `W`

### 6. `false` → `False` (×2 dans les parametrize)
- Commande globale : `:%s/\bfalse\b/False/g<Entrée>`

### 7. `Self` → `self` dans `test_empty_string(Self)`
- `/def test_empty_string<Entrée>`
- Place-toi sur `S` de `Self` → `~`

### 8. Ajouter le décorateur manquant sur `test_password_strength`
- La fonction `test_password_strength` n'a pas de décorateur `@pytest.mark.parametrize`.
- Va sur la ligne `/def test_password_strength<Entrée>`
- Ouvre une ligne au-dessus : `O`
- Tape : `@pytest.mark.parametrize("password, expected", [`
- `<Echap>` — attends, le décorateur est déjà là (ligne au dessus). Rien à faire ici.

### 8. (reformulé) `test_power` — corriger la valeur attendue : `2^8 = 256` mais l'appel est `power(2, 8)` ✅
- Pas de correction nécessaire.

### 8. Corriger `colect()` → `collect()` dans `get_errors`
- Ce bug n'est pas dans ce fichier — il est dans l'exercice 16. Ignore.

### 8. Supprimer les faux commentaires `# ============...` avec une commande globale
- Si tu veux alléger le fichier : `:g/^# ===/d<Entrée>`
- **Optionnel** — à toi de choisir.

---

## Résultat final attendu (corrections obligatoires)

```python
    def setup_method(self):         # plus setup_methode

    def test_addition_negative(self):   # plus negatif

    def test_subtraction(self):
        result = self.calc.subtract(10, 4)   # plus substract

        with pytest.raises(ValueError):      # plus With

    assert self.validator.is_valid_ip("999.999.999.999") == False  # plus false

    def test_empty_string(self):     # plus Self
```

---

```
cp exercices/exercice14/exercice14.txt soumissions/exercice14.txt
```
