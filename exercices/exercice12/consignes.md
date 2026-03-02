# Exercice Vim 12 — Ansible Playbook

Ouvre le fichier dans Vim :

```
vim exercices/exercice12/exercice12.txt
```

> `:set number` pour afficher les numéros de ligne

---

## Nouvelles commandes

| Commande | Action |
|----------|--------|
| `>>` | Indenter la ligne courante d'un niveau |
| `<<` | Désindenter la ligne courante |
| `==` | Auto-indenter la ligne courante |
| `>ip` | Indenter le paragraphe courant |
| `:set shiftwidth=2` | Définir l'indentation à 2 espaces |

---

## Modifications à effectuer

### 1. `Hosts` → `hosts` (ligne 6)
- `/^  Hosts<Entrée>` puis `~`

### 2. `become: Yes` → `become: yes`
- `/become: Yes<Entrée>` — place-toi sur `Y` → `~`

### 3. `max_connections: 99` → `max_connections: 100`
- `/max_connections: 99<Entrée>` — place-toi sur `99` → `Ctrl+A`

### 4. `debug_mode: True` → `debug_mode: false` (désactiver en prod !)
- `/debug_mode<Entrée>` — `ciw` sur `True` → tape `false<Echap>`

### 5. `Tasks` → `tasks` (ligne 17)
- `/^  Tasks<Entrée>` → `~`

### 6. `install required` → `Install required` (convention Ansible : majuscule)
- `/install required<Entrée>` → `~`

### 7. `Git` → `git` dans la liste de packages
- `/        - Git<Entrée>` → `~`

### 8. `pressent` → `present`
- `/pressent<Entrée>` → `ciw` → tape `present<Echap>`

### 9. `User:` → `user:` (module Ansible)
- `/^    - name: Create application user<Entrée>` — descends d'une ligne : `j`
- `/^      User:<Entrée>` → `~`

### 10. `directori` → `directory`
- `/directori<Entrée>` → `ciw` → tape `directory<Echap>`

### 11. `version: mane` → `version: main`
- `/mane<Entrée>` → `r i` (remplace `e` par `i`)... attends : `ciw` → tape `main<Echap>`

### 12. `Notify` → `notify`
- `/Notify<Entrée>` → `~`

### 13. `state: lynk` → `state: link`
- `/lynk<Entrée>` → `ciw` → tape `link<Echap>`

### 14. `Handlers` → `handlers`
- `/^  Handlers<Entrée>` → `~`

---

## Résultat final attendu (corrections clés)

```yaml
- name: Provision web servers
  hosts: webservers
  become: yes
  vars:
    ...
    max_connections: 100
    debug_mode: false

  tasks:
    - name: Update apt cache
    ...
    - name: Install required packages
      apt:
        name:
          - nginx
          - python3
          - python3-pip
          - git
        state: present
    - name: Create application user
      user:
    ...
    - name: Create app directory
      file:
        state: directory
    ...
    - name: Clone application repository
      git:
        version: main
    ...
      notify: reload nginx
    - name: Enable nginx site
      file:
        state: link

  handlers:
    - name: reload nginx
```

---

```
cp exercices/exercice12/exercice12.txt soumissions/exercice12.txt
```
