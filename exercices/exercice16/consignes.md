# Exercice Vim 16 — Rust : Log Analyzer

Ouvre le fichier dans Vim :

```
vim exercices/exercice16/exercice16.txt
```

---

## Contexte

Code Rust d'un analyseur de logs. Rust est extrêmement strict sur la syntaxe et les types — chaque faute de frappe est une erreur de compilation. Ton éditeur (Vim) est ton premier outil de défense !

---

## Nouvelles commandes

| Commande | Action |
|----------|--------|
| `das` | Supprimer une phrase entière (delete a sentence) |
| `%` | Sauter au délimiteur correspondant `{` `}` `(` `)` |
| `]]` | Sauter à la prochaine `{` de niveau 0 (prochaine fonction/impl) |
| `[[` | Sauter à la `{` de niveau 0 précédente |
| `:%s/\<mot\>/nouveau/g` | Substitution avec délimiteurs de mots stricts |

---

## Modifications à effectuer

### 1. `HasMap` → `HashMap` (×4 dans le fichier)
- Commande : `:%s/HasMap/HashMap/g<Entrée>`

### 2. `#[derive(Debg` → `#[derive(Debug`
- `/Debg<Entrée>` → `ciw` → tape `Debug<Echap>`

### 3. `levvel` → `level` (×3 dans le fichier — dans la struct et ses usages)
- Commande : `:%s/levvel/level/g<Entrée>`

### 4. `selff` → `Self` dans le `impl`
- `/selff<Entrée>` → `ciw` → tape `Self<Echap>`

### 5. `self.level` dans `is_error` — après correction de `levvel`, vérifier que la méthode est cohérente
- `/self\.level<Entrée>` — la ligne `self.levvel == "ERROR" || self.level == "CRITICAL"` a une incohérence.
- Après le `:%s/levvel/level/g`, les deux occurrences seront `self.level` — c'est correct.

### 6. `io::Ressult` → `io::Result`
- `/Ressult<Entrée>` → `ciw` → tape `Result<Echap>`

### 7. `colect()` → `collect()`
- `/colect<Entrée>` → `ciw` → tape `collect<Echap>`

### 8. `fn maine()` → `fn main()`
- `/fn maine<Entrée>` → place-toi sur `e` → `x`

---

## Résultat final attendu (corrections clés)

```rust
use std::collections::HashMap;

#[derive(Debug, Clone)]
pub struct LogEntry {
    pub level: String,
    ...
}

impl LogEntry {
    pub fn new(...) -> Self {
        LogEntry {
            level: level.to_string(),
            ...
        }
    }

    pub fn is_error(&self) -> bool {
        self.level == "ERROR" || self.level == "CRITICAL"
    }
}

pub struct LogAnalyzer {
    entries: Vec<LogEntry>,
    stats: HashMap<String, u32>,
}

impl LogAnalyzer {
    pub fn new() -> Self {
        LogAnalyzer {
            stats: HashMap::new(),
            ...
        }
    }

    pub fn load_file(&mut self, path: &str) -> io::Result<()> {
        ...
        *self.stats.entry(entry.level.clone()).or_insert(0) += 1;

    pub fn get_errors(&self) -> Vec<&LogEntry> {
        self.entries.iter().filter(|e| e.is_error()).collect()
    }

    pub fn get_stats(&self) -> &HashMap<String, u32> {

fn main() {
```

---

```
cp exercices/exercice16/exercice16.txt soumissions/exercice16.txt
```
