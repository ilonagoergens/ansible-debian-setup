#!/bin/bash

# 1️⃣ Repository klonen
git clone <repo-url>
cd ansible-debian-setup

# 2️⃣ SSH-Schlüssel einrichten
chmod 600 ~/.ssh/universall.pem

# 3️⃣ Ansible installieren (falls nicht vorhanden)
sudo apt update && sudo apt install -y ansible

# 4️⃣ Konfigurationsdateien prüfen
# (Öffne die config.cfg und hosts, um sicherzustellen, dass die SSH-Details und der Benutzername korrekt sind)
# (Falls dein Benutzer nicht ubuntu ist, ändere ansible_user entsprechend)

# 5️⃣ Playbook ausführen
ansible-playbook -i hosts playbook.yml

# 6️⃣ Überprüfung der Installation
nginx -v
curl --version
git --version

ls -l /tmp/example.txt
cat /tmp/example.txt

# Troubleshooting
ansible all -m ping -i hosts
ansible --version
ansible-playbook -i hosts playbook.yml -vvv
