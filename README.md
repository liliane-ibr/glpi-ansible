GLPI Ansible
Ce projet permet d’automatiser l’installation de GLPI sur un serveur Debian à l’aide d’Ansible. L’objectif est de fournir un déploiement rapide, fiable et reproductible sans intervention manuelle.

💡 Prérequis
1️⃣ Installer Ansible sur votre machine de contrôle (Debian Bookworm)
Voici les commandes utilisées pour installer Ansible depuis les backports de Debian Bookworm :


sudo apt update && sudo apt upgrade -y
sudo apt install -y software-properties-common
echo 'deb http://deb.debian.org/debian bookworm-backports main' | sudo tee /etc/apt/sources.list.d/backports.list
sudo apt update
sudo apt install -y -t bookworm-backports ansible
ansible --version


3️⃣ Serveur cible
Distribution : Debian (testé sur Debian 12)

Accès SSH fonctionnel

Paquets système à jour :
sudo apt update && sudo apt upgrade -y

🚀 Lancement du déploiement
Une fois prêt, exécutez le playbook principal :

ansible-playbook playbooks/install_glpi.yml -i inventory


🛠 Architecture du projet
Le projet est organisé de manière modulaire :

roles/ : rôles Ansible pour séparer les étapes de l’installation :

apache : installation et configuration d’Apache

php : installation des paquets PHP nécessaires

mariadb : installation et configuration de MariaDB

security : bonnes pratiques de sécurité

glpi : téléchargement et configuration de GLPI

playbooks/install_glpi.yml : playbook principal qui orchestre les rôles.

inventory : liste des hôtes cibles.

group_vars/all.yml : variables globales pour personnaliser l’installation.
