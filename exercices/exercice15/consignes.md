# Exercice Vim 15 — Terraform / Infrastructure as Code

Ouvre le fichier dans Vim :

```
vim exercices/exercice15/exercice15.txt
```

---

## Contexte

Fichier Terraform HCL pour déployer une infra AWS. Contient des erreurs de casse, des fautes de frappe et des problèmes de sécurité (SSH ouvert à tous !).

---

## Nouvelles commandes

| Commande | Action |
|----------|--------|
| `:vimgrep /motif/ %` | Chercher un motif dans le fichier courant |
| `:copen` | Ouvrir la quickfix list (résultats de vimgrep) |
| `:cnext` / `:cprev` | Occurrence suivante / précédente dans quickfix |
| `*` | Chercher le mot sous le curseur (vers l'avant) |
| `#` | Chercher le mot sous le curseur (vers l'arrière) |

---

## Modifications à effectuer

### 1. `encrypt = True` → `encrypt = true` (HCL : booléens en minuscules)
- `/encrypt = True<Entrée>` → place-toi sur `T` → `~`

### 2. `discription` → `description`
- `/discription<Entrée>` → `ciw` → tape `description<Echap>`

### 3. `error_massage` → `error_message`
- `/error_massage<Entrée>` → `ciw` → tape `error_message<Echap>`

### 4. `enable_dns_hostnames = True` → `true`
- `/enable_dns_hostnames<Entrée>` → place-toi sur `T` → `~`

### 5. `Environnement` → `Environment` dans les tags VPC
- `/Environnement<Entrée>` → `ciw` → tape `Environment<Echap>`

### 6. `Tier = "Publik"` → `Tier = "Public"`
- `/Publik<Entrée>` → place-toi sur le `k` → `r c` (remplace `k` par `c`)

### 7. `description = "SSH acces"` → `description = "SSH access"`
- `/SSH acces<Entrée>` → place-toi à la fin de `acces` → `a s<Echap>`

### 8. Sécurité critique — restreindre le SSH (0.0.0.0/0 = tout internet !)
- Cherche le bloc SSH : `/SSH acces<Entrée>`
- La ligne `cidr_blocks = ["0.0.0.0/0"]` sous le SSH doit devenir `cidr_blocks = ["10.0.0.0/8"]`
- `/from_port   = 22<Entrée>` puis `2j` pour aller sur la ligne cidr_blocks du SSH
- `ci[` puis tape `"10.0.0.0/8"<Echap>`

### 9. Utiliser `*` pour trouver tous les `HasMap` (exercice de navigation)
- Place le curseur sur `HasMap` et appuie sur `*` pour voir toutes les occurrences
- (Ce mot est dans l'exercice 16, pas ici — utilise `*` sur `True` pour voir les occurrences restantes)

---

## Résultat final attendu (corrections clés)

```hcl
  backend "s3" {
    encrypt        = true
    ...
  }

variable "aws_region" {
  description = "AWS region"   # plus discription

variable "environment" {
  validation {
    error_message = "..."      # plus error_massage

resource "aws_vpc" "main" {
  enable_dns_hostnames = true  # plus True
  tags = {
    Environment = var.environment   # plus Environnement

resource "aws_subnet" "public" {
  tags = {
    Tier = "Public"            # plus Publik

  ingress {
    description = "SSH access" # plus acces
    cidr_blocks = ["10.0.0.0/8"]  # plus 0.0.0.0/0 !
```

---

```
cp exercices/exercice15/exercice15.txt soumissions/exercice15.txt
```
