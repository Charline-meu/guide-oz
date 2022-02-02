---
title: "Linux"
date: 2021-08-24T14:21:32+02:00
draft: false
---

# Linux
## Installation
Chaque distribution de Linux a sa propre méthode d'installation. Référez-vous donc à celle de votre distribution.

### Arch
Installez Yay.
```shell
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -si
```
Ensuite installez mozart.
```shell
yay -Sy mozart2
```
### Ubuntu
Tutoriel complet [ici](https://help.ubuntu.com/community/Mozart)

## Lancer l'environnement de développement
```shell
oz
```
