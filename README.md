# Brief13 
#Durcissement du systeme Linux

## Rôle Ansible - ANSSI-RECOM:


Utiliser le document fourni par l'ANSSI pour traduire les recommandations de sécurité en tâches Ansible.

Se concentrer uniquement sur les niveaux de durcissement "Minimum" et "Intermédiaire".


- Pour le durcissement Minimum selon les recommandation de l'ANSSI:

https://github.com/RedHatOfficial/ansible-role-rhel8-anssi_bp28_minimal

- Pour le durcissement Intermédiaire selon les recommandation de l'ANSSI:

https://github.com/RedHatOfficial/ansible-role-rhel8-anssi_bp28_intermediary


## Préparation de l'Environnement de Déploiement:


### Infrastructure Azure avec Terraform:

Dans le même dossier que playbook.yml, utiliser Terraform pour déployer un groupe de ressources Azure avec un réseau virtuel (VNet) et ses sous-réseaux.
Création de Machine Virtuelle Azure:

Ajouter à Terraform la création d'une machine virtuelle Azure (azurerm_virtual_machine).
Utiliser une clé SSH générée préalablement pour faciliter les opérations.
Intégration Ansible dans Terraform:

Dans le bloc de provisionnement azurerm_virtual_machine, ajouter un provisionneur local-exec qui:
Exécute les commandes ansible-galaxy pour installer les dépendances.
Lance le ansible-playbook pour appliquer les tâches.
Veiller à bien configurer le playbook Ansible pour qu'il cible la machine virtuelle Azure créée.
Déploiement Automatique:

Après exécution de la commande terraform apply, l'infrastructure doit se déployer selon la description.
Le rôle Ansible doit être appliqué automatiquement sur la machine virtuelle Azure.

Dans ce repo git :

- le fichier terraform pour déployer l'infrastructure avec la vm dont ansible durci automatiquement le systeme Linux basé sur une RedHat 8.8 selon la recommandation ANSSI.
- Le rapport complet fournis par l'outil de test de sécurité OPENScap dans le fichier report-1.html



## Durcissement du systeme Linux suivant les recommandation ANSSI Intermédiaire 
**Score OPENScap à 51%**

```
      "sudo dnf -y update",
      "sudo dnf install -y ansible",
      "echo '[localhost]' > inventory.ini",
      "sudo ansible-galaxy role install RedHatOfficial.rhel8_anssi_bp28_intermediary",
      "sudo yum install -y scap-workbench",
      "echo '- hosts: all\n  roles:\n     - { role: RedHatOfficial.rhel8_anssi_bp28_intermediary }' > playbook.yml",
      "sudo ansible-playbook -i 'localhost,' -c local playbook.yml",
```

![](https://github.com/simplon-nicolasmarty/Brief13-oscap-redhat/blob/main/Capture%20d%E2%80%99%C3%A9cran%20du%202023-11-02%2009-25-10.png)

![](https://github.com/simplon-nicolasmarty/Brief13-oscap-redhat/blob/main/Capture%20d%E2%80%99%C3%A9cran%20du%202023-11-02%2009-31-21.png)

![](https://github.com/simplon-nicolasmarty/Brief13-oscap-redhat/blob/main/Capture%20d%E2%80%99%C3%A9cran%20du%202023-11-02%2009-31-55.png)

Résultat du rapport au niveau intermédiaire selon les recommandation de l'ANSSI :

![](https://github.com/simplon-nicolasmarty/Brief13-oscap-redhat/blob/main/Capture%20d%E2%80%99%C3%A9cran%20du%202023-11-02%2009-43-18.png)


## Durcir d'avantage le systeme Linux REdHat

Résolution des failles potentielles avec l'outil OSCAP.

**Score du rapport OPENScap à 91%**

commande à intégrer :
```
sudo oscap xccdf eval --profile hipaa --remediate /usr/share/xml/scap/ssg/content/ssg-rhel8-ds.xml
```
Corrections appotorté au système

![](https://github.com/simplon-nicolasmarty/Brief13-oscap-redhat/blob/main/Capture%20d%E2%80%99%C3%A9cran%20du%202023-11-02%2016-07-37.png)

Résultat du test OPENScap après l'application

![](https://github.com/simplon-nicolasmarty/Brief13-oscap-redhat/blob/main/Capture%20d'%C3%A9cran%202023-10-23%20135530.png)
