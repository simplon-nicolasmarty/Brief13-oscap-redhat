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

![anssi.png](https://hackmd.io/_uploads/SJTahNbma.png)

## Durcissement du systeme Linux

**Score OPENScap à 91%**
```
sudo oscap xccdf eval --profile hipaa --remediate /usr/share/xml/scap/ssg/content/ssg-rhel8-ds.xml
```
![Capture d’écran du 2023-11-02 16-07-37.png](https://hackmd.io/_uploads/rkEaiVZ7T.png)

![Capture d'écran 2023-10-23 135530.png](https://hackmd.io/_uploads/rJGcn4bmT.png)
