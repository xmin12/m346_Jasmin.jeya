# KN02 18.09.2023 


# KN03: Cloud-init und AWS

## A) Cloud-init Datei Verstehen

```YAML 
users:                                                               # Benutzerkonfiguration
  - name: ubuntu                                                     # Benutzername
    sudo: ALL=(ALL) NOPASSWD:ALL                                     # sudo-regeln für diesen benutzer
    groups: users, admin                                             # Benutzer ist Mitglied in den Gruppen "users" und "admin"
    home: /home/ubuntu                                               # Benutzerverzeichnis: /home/ubuntu
    shell: /bin/bash                                                 # Verwendete Shell: /bin/bash
    ssh_authorized_keys:                                             # SSH-öffentlicher Schlüssel zur Authentifizierung
      - ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC0WGP1EZykEtv5YGC9nMiPFW3U3DmZNzKFO5nEu6u
        ozEHh4jLZzPNHSrfFTuQ2GnRDSt+XbOtTLdcj26+iPNiFoFha42aCIzYjt6V8Z+SQ9pzF4jPPzxw
        XfDdkEWylgoNnZ+4MG1lNFqa8aO7F62tX0Yj5khjC0Bs7Mb2cHLx1XZaxJV6qSaulDuBbLYe8QUZXkMc
        7wmob3PM0kflfolR3LE7LResIHWa4j4FL6r5cQmFlDU2BDPpKMFMGUfRSFiUtaWBNXFOWHQBC2+
        /X2KyemqdMvdKXnCfrzadHuSSJYEzD64Cve5Zl9yVvY4AqyBD aws-key    # Öffentlicher SSH-Schlüssel
ssh_pwauth: false                                                    # SSH-Passwort-Authentifizierung ist deaktiviert
disable_root: false                                                  # Das Deaktivieren des Root-Benutzers ist deaktiviert
package_update: true                                                 # Paketaktualisierungen werden durchgeführt
packages:                                                            # Zusätzliche Pakete, die installiert werden
  - curl                                                             # Paket: curl
  - wget                                                             # Paket: wget

```


## B) SSH-Key und Cloud-init

- Sihe bei der Repo KN03 File "#cloud-config" da sieht man .yaml mein Cloud-init.
  
- ### Ein Screenshot der Details der Instanz. Scrollen Sie so weit runter,
  ### dass das Feld "Key pair assigned at launch", sichtbar ist.
  ![Screenshot 2023-09-25 092612](https://github.com/xmin12/m346_Jasmin.jeya/assets/112725311/186c29e1-6c72-49f1-97e5-c15cfaee87cb)

- ## Screenshot mit dem ssh-Befehl und des Resultats unter Verwendung des 1 Schlüssels.
  ![Screenshot 2023-09-25 092724](https://github.com/xmin12/m346_Jasmin.jeya/assets/112725311/eaac21fe-8801-4743-952c-560d01c5a837)

- ## Screenshot mit dem ssh-Befehl und des Resultats unter Verwendung des 2 Schlüssels.
  ![Screenshot 2023-09-25 092806](https://github.com/xmin12/m346_Jasmin.jeya/assets/112725311/10ebadc1-7c15-4a85-bc4f-64af30cfd0d2)


- ## Screenshot mit dem Auszug aus dem Cloud-Init-Log.
  ![Screenshot 2023-09-25 093222](https://github.com/xmin12/m346_Jasmin.jeya/assets/112725311/a57289c0-b056-4486-b9af-e52ba34ebf0b)

## C) Template

- Sihe bei der Repo KN03 File "C)cloud-init2" da sieht man .yaml File mit beide éffentliche Keys von Lehrer und meinen.

## D) Auftrennung von Web- und Datenbankserver

* DB
  - Der Befehl und die CLI von mysql zeigt.
    ![Screenshot 2023-09-25 110948](https://github.com/xmin12/m346_Jasmin.jeya/assets/112725311/0503cfc2-952a-4a88-97e2-1fae74eb3834)
    
  - Sihe einen Screenshot des Resultats der Befehl ist nicht Sichtbar.
  ![Screenshot 2023-09-25 114814](https://github.com/xmin12/m346_Jasmin.jeya/assets/112725311/4af00104-34b3-471e-8fbe-47c5b8850ba2)


* WebServer
  - index.html
  ![Screenshot 2023-10-23 093548](https://github.com/xmin12/m346_Jasmin.jeya/assets/112725311/8791a33f-2fa6-4499-8549-4a4aee38dc93)

  - info.php
  ![Screenshot 2023-10-23 093754](https://github.com/xmin12/m346_Jasmin.jeya/assets/112725311/503fc1b7-8876-46ad-ba95-cc0d09dd14fd)

  - db.php
  ![Screenshot 2023-10-23 093820](https://github.com/xmin12/m346_Jasmin.jeya/assets/112725311/f78b2fe4-b707-430a-8641-51f6fbec3031)

  - http://3.93.149.30/adminer/
  ![image](https://github.com/xmin12/m346_Jasmin.jeya/assets/112725311/51919b44-9edf-47cd-8cae-608192c291ca)

