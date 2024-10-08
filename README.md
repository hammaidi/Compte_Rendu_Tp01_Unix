# Compte_Rendu_Tp01_Unix   HAMMAIDI KARIM


2 Post-Installation

2.1  
configuration du ssh:

- on utlilse: apt update pour rechercher les paquets ssh et les mettres a jours
- pour vérifier que les paquets SSH sont disponibles et connaître son statut, on exécute la commande suivante :apt search ssh 
-on l'installe avec: apt install openssh-server
  Pour lancer le ssh: service ssh start

- on tape la commande :systemctl status ssh  
->Si la ligne 'Active: active (running)' cela montre que le service SSH est bien actif et fonctionne correctement. 




2.2  CONNEXION


Maintenant que que le SSH est actif, nous pouvons essayer de nous connecter à la machine virtuelle depuis la machine hôte en utilisant la commande SSH, avec : ssh root@adresse_IP_de_la_VM

- Pour chercher l'adresse ip de la machine virtuele à l'aide de cette commande: ip a , L'adresse IP est indiquée après 'inet', en l'occurance ici l'adresse ip est '10.0.2.15'
 
- Nous pouvons à présent connecter les 2 machines a laide de cette commande  ssh root@10.0.2.15


-> Je recois un message d'avertissement
'Are you sure you want to continue connecting (yes/no)? yes'

Authenticité de l'hôte : Lorsqu'on  s'est connecté à l'adresse IP de la machine virtuelle (10.0.2.15), il a été signalé que l'authenticité de l'hôte ne pouvait pas être établie. Cela est normal car lors de la première connexion, le client SSH n'a jamais vu cet hôte avant.


2.3)


le resultat est: 357 paquets.


2.4)
Voici le résultat:

Sys. de fichiers    Taille  Utilisé  Dispo  Uti% Monté sur
dev                 965M       0  965M    0% /dev
tmpfs               197M     556K   197M    1% /run
/dev/sda1           9,1G   1,2G   7,4G   14% /
tmpfs               984M       0   984M    0% /dev/shm
tmpfs               5,0M       0   5,0M    0% /run/lock
/dev/sda2           3,6G     40K   3,4G   11% /home
/dev/sda3          921M     86M   732M   11% /var/log
tmpfs               197M       0   197M    0% /run/user/0


-Commande: df -h pour vérifier l'utilisation de l'espace disque, les résultats montrent que la partition racine est utilisée à 14%.


2.5)


Commandes à utiliser:

-Locales : echo $LANG            = 'fr_FR.UTF-8' 

-Nom de la machine : hostname    =  'debian'

-Domaine : hostname -d           = 'ufr-info-p6.jussieu.fr'

Utilisateurs : cat /etc/passwd | grep -vE 'nologin|sync' = 'root:x:0:0:root:/root/bin/bash'

Vérification des fichiers de mot de passe : cat /etc/shadow | grep -vE ':*\:|:!:|*\:'

Espace disque : df -h = 14%



-La commande echo $LANG m'a permis de vérifier les paramètres régionaux du système.
-En utilisant hostname, j'ai pu identifier le nom de la machine.
-La commande hostname -d m'a montré le domaine associé à cette machine.
-Pour vérifier les dépôts, j'ai exécuté cat /etc/apt/sources.list | grep -v -E '#|$', ce qui m'a donné la liste des dépôts configurés.
-J'ai également vérifié les utilisateurs et leurs permissions avec cat /etc/passwd | grep -vE 'nologin|sync'.
-Enfin, j'ai utilisé df -h pour vérifier l'espace disque et fdisk -l pour voir les partitions du disque.


3.1)

-C'est un fichier qui contient des réponses prédéfinies aux questions que l'installateur Debian pose pendant l'installation.
ça sert à automatiser l'installation : Au lieu de répondre manuellement à chaque question (comme le nom de l'utilisateur, le mot de passe, la configuration réseau, etc.), le système utilise ce fichier pour remplir automatiquement les réponses.

3.2)

la commande: passwd root

3.3) 

Lancer GParted :

-Une fois que nous sommes dans l'environnement live, ouvrez GParted. Vous verrez toutes vos partitions listées.
-Redimensionner la partition racine :
Sélectionnez la partition racine (généralement /dev/sda1 ou /dev/sda2, selon la configuration).




Sources utilisés pour le tp: chatGpt
