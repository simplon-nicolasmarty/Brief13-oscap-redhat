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


![Capture d’écran du 2023-11-02 09-25-10.png](https://hackmd.io/_uploads/r1hZhNbmp.png)

![Capture d’écran du 2023-11-02 09-31-21.png](https://hackmd.io/_uploads/Skh-2EWQ6.png)

![Capture d’écran du 2023-11-02 09-31-55.png](https://hackmd.io/_uploads/H1jWn4W7T.png)

![anssi.png]([https://hackmd.io/_uploads/SJTahNbma.png](https://media.discordapp.net/attachments/990915126301450251/1169661538198634557/anssi.png?ex=65563731&is=6543c231&hm=3893c5ad2e0eeb960b0631651744ca9463457c51ddeb6be66581eec39262db20&=&width=1440&height=533))

## Durcissement du systeme Linux

**Score OPENScap à 91%**
```
sudo oscap xccdf eval --profile hipaa --remediate /usr/share/xml/scap/ssg/content/ssg-rhel8-ds.xml
```
![Capture d’écran du 2023-11-02 16-07-37.png](https://hackmd.io/_uploads/rkEaiVZ7T.png)

![91]([/chemin/access/image.jpg](https://github.com/simplon-nicolasmarty/Brief13-oscap-redhat/blob/main/Capture%20d'%C3%A9cran%202023-10-23%20135530.png)https://github.com/simplon-nicolasmarty/Brief13-oscap-redhat/blob/main/Capture%20d'%C3%A9cran%202023-10-23%20135530.png "91")
