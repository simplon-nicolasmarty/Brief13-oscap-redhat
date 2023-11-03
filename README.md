# Brief13 

Durcissement du systeme Linux


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

![](https://github.com/simplon-nicolasmarty/Brief13-oscap-redhat/blob/main/Capture%20d%E2%80%99%C3%A9cran%20du%202023-11-02%2009-43-18.png)


## Durcissement du systeme Linux

**Score OPENScap à 91%**
```
sudo oscap xccdf eval --profile hipaa --remediate /usr/share/xml/scap/ssg/content/ssg-rhel8-ds.xml
```

![](https://github.com/simplon-nicolasmarty/Brief13-oscap-redhat/blob/main/Capture%20d%E2%80%99%C3%A9cran%20du%202023-11-02%2016-07-37.png)

![](https://github.com/simplon-nicolasmarty/Brief13-oscap-redhat/blob/main/Capture%20d'%C3%A9cran%202023-10-23%20135530.png)
