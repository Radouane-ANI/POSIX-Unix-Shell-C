![Logo du projet](banniere.png)

# 🐚 POSIX-Unix-Shell-C (fsh) — Interpréteur de Commandes Unix en C

[![Language](https://img.shields.io/badge/Language-C99-00599C.svg?logo=c)](https://en.wikipedia.org/wiki/C99)
[![Standard](https://img.shields.io/badge/Standard-POSIX-brightgreen.svg)]()
[![OS](https://img.shields.io/badge/OS-Linux%20%2F%20UNIX-FCC624.svg?logo=linux&logoColor=black)](https://kernel.org/)
[![Build](https://img.shields.io/badge/Build-Makefile-purple.svg)]()

**fsh** est un interpréteur de commandes Unix complet développé en **C**, conçu dans le strict respect des spécifications de l'API standard **POSIX** (gestion des processus, signaux et redirections de flux).

---

## ⚡ Fonctionnalités Clés

- **Exécution et Contrôle de Processus** :
  - Lancement des exécutables Unix via la combinaison `fork()` et `execvp()`.
  - Surveillance et synchronisation des processus enfants via `waitpid()`.
- **Pipelines et Redirections de Flux** :
  - Pipelines multi-commandes arbitrairement longs (`cmd1 | cmd2 | cmd3`) via la primitive système `pipe()`.
  - Redirections d'entrée/sortie standard et d'erreur (`<`, `>`, `>>`, `2>`) avec duplication de descripteurs de fichiers via `dup2()`.
- **Gestion Robuste des Signaux POSIX** :
  - Interception des interruptions clavier `SIGINT` (Ctrl+C) pour ne pas tuer le shell parent.
  - Capture et traitement asynchrone de `SIGCHLD` pour éliminer systématiquement la création de processus zombies.
- **Structures de Contrôle Avancées** :
  - Support natif des boucles itératives `for var in list ; do ... done`.
  - Évaluation de conditions `if [ ... ] ; then ... else ... fi`.

---

## 📂 Architecture Logicielle

- `fsh.c` : Boucle principale d'évaluation REPL (*Read-Eval-Print Loop*) et analyse syntaxique de la ligne de commande.
- `externe.c` : Gestion des commandes externes, résolution du `PATH` et exécution sous processus enfants.
- `for.c` : Moteur d'interprétation et d'exécution des boucles `for`.
- `free.c` : Gestion rigoureuse de la mémoire et libération des structures allouées (zéro fuite mémoire Valgrind).

---

## 🚀 Installation & Compilation

### Prérequis
Un compilateur C (`gcc` ou `clang`) et l'outil `make` sur environnement Linux / Unix.

### Compilation
```bash
git clone https://github.com/Radouane-ANI/POSIX-Unix-Shell-C.git
cd POSIX-Unix-Shell-C
make
```

### Lancement
```bash
./fsh
```

---

## 👥 Auteur
- **Radouane Aouini** — Master Cryptologie, Calcul Haute Performance et Algorithmie (CCA) ([LinkedIn](https://www.linkedin.com/in/radouane-aouini-b14bab348))
