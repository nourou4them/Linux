# Procédure d'installation de CentOS sur une VM (A traduire en anglais)  

## 1 - Installer VirtualBox  

Comme indiqué sur sa page, [Wikipedia](<https://fr.wikipedia.org/wiki/Oracle_VM_VirtualBox> "Page Wikipedia de VirtualBox"), VirtualBox est un logiciel libre de virtualisation publié par Oracle.  
Lien de téléchargement : <https://www.virtualbox.org/wiki/Downloads>  


## 2 - Télécharger CentOS 7  



## 3 - Créer une nouvelle machine  

Y intégrer CentOS 7 : DVD mirroir  


## 4 - Installer l'interface graphique GNOME 

  Avant tout, il faut activer la connection par nmtui  

  En même temps, réduire la taille des icônes de l'interface  

  Automatiser le lancement automatique de l'interface graphique  


## 5 - Intégrer les extensions  

    VirtualBox guest additions  

A - Téléchargements à faire  

    Faire la mise à jour yum update  
    installer Development tools  
    installer kernel-devel  
    installer epel-release  
    installer dkms  

B - Créer une place pour les extensions

Créer par mkdir  
Monter l'ISO  

## 6 - Importer le script

Créer un dossier dans C:\ ou un autre drive  
Créer un dossier partagé sur VirtualBox , config de la machine  
Lier les deux dossiers  
Les délier ensuite  


## 7 - Créer un network repository  

    Intaller le package httpd  


## 7 - Installer GETH sur CentOS 7  
Solution 1  

    Installer Golang
    Installer gmp-devel
    Cloner go à partir u github d'Ethereum
    cd go-ethereum
    make geth
    ls -al build/bin/geth

    Lancer 
    $ .go-ethereum/build/bin/geth

Solution 2  

    Télécharger l'archive de go sur le site officiel
    <https://golang.org/dl/>  

A Faire!!!  
Extraire l'archive et l'installer là où on aura choisi
Continuer la procédure : <https://tecadmin.net/install-go-lang-on-centos/>



### A  

1. Téléchargement du code source GO (archive) && build  

        ARCHIVE= ... && curl https:// .. && tar zxvf - && 
        Fait

2. Copie sur le système  

        cp -R $HOME/.../go /usr/local    ---> /usr/local/go/.. 

Fait : Fichier déplacé : /usr/local/go  

4. Créer l'utilisateur et le groupe GO  

        sudo useradd go:go  ??? adduser ??  \
        #useradd -m <utilisateur>      // création d'un utilisateur avec sa home directory

Fait :Création de l'utilisateur GO => usergo  
Création du groupe GO => groupgo  
Ajout des utilisateurs user et usergo à groupgo  

5. Se rajouter au groupe GO  

        sudo groupadd user go ??  \
        ajoute supprime un utilisateur à un groupe
        #gpasswd -d <user> <group>
        -a pour ajouter

6. Changer le owner en GO:GO  

        sudo chown -R go:go /usr/local/go 

FAIT 

7. Inscrire Go dans le bsh profile

        GO_WORKSPACE=${HOME}/workspace 
        mkdir -p ${GO_WORKSPACE}
        echo -e "export PATH=${PATH}:${GO_PATH}\nexport GO_PATH=${GO_WORKSPACE}" >> ~/.bash_profile
        source ~/.bash_profile

FAIT !

##+ tester dans $HOME

    récuperer un exemple de fichier 'toto.go' du web avec une fonction main() dedans 
    $ go build toto.go 
    $ ./toto
    $ echo $?   ---> 0 == SUCCESS, !0 == FAILURE
    0su


    echo -e "package main\n\n\nimport \"fmt\"\nfunc main() {\n\tfmt.Println("hello world")\n}" > main.go && go build main.go && ./main.go && rm -f ./main 

