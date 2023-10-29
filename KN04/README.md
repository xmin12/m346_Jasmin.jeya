# KN04: Cloud-init / Storage

## A) Bild erstellen und auf S3 hosten

### Screenshot der S3-Objekte im Bucket
![Screenshot 2023-10-23 101414](https://github.com/xmin12/m346_Jasmin.jeya/assets/112725311/139e5312-9920-4af2-bc5c-edcb3422cab9)
### Screenshot des Bildes im Browser (mit sichtbarer URL)
![Screenshot 2023-10-23 112025](https://github.com/xmin12/m346_Jasmin.jeya/assets/112725311/bac7f5a0-476b-4bf4-b4d3-5d16e0243ca1)

## B) Web-Server mit PHP-Seite hinzufügen
- Neues Cloud-Init für die Web-Instanz
```YAML
users:
  - name: ubuntu
    sudo: ALL=(ALL) NOPASSWD:ALL
    groups: users, admin
    home: /home/ubuntu
    shell: /bin/bash
    ssh_authorized_keys:
      - ssh-rsa
        AAAAB3NzaC1yc2EAAAADAQABAAABAQC0WGP1EZykEtv5YGC9nMiPFW3U3DmZNzKFO5nEu6uozEHh4jLZzPNHSrfFTuQ2GnRDSt+XbOtTLdcj26+iPNiFoFha42aCIzYjt6V8Z+SQ9pzF4jPPzxwXfDdkEWylgoNnZ+4MG1lNFqa8aO7F62tX0Yj5khjC0Bs7Mb2cHLx1XZaxJV6qSaulDuBbLYe8QUZXkMc7wmob3PM0kflfolR3LE7LResIHWa4j4FL6r5cQmFlDU2BDPpKMFMGUfRSFiUtaWBNXFOWHQBC2+uKmuMPYP4vJC9sBgqMvPN/X2KyemqdMvdKXnCfrzadHuSSJYEzD64Cve5Zl9yVvY4AqyBD
        aws-key
      - ssh-rsa
        AAAAB3NzaC1yc2EAAAADAQABAAABAQDDEirijxHZRaN8tdYpBI0YFt9dZuHWLaAJ+WId1Zx/F46AJSwv0nZbQHf8cSvjWrNAsZXe/OxbLzextUsONanKsCdoIdppHgXersHCNlliHs0HlDL3TdWLfVgRraTEf17OsyscW+abqMrnPx5M4Q0IBDqZKccpuGJHD+5BssWIv+qevOOlU2FbLSk3Y3ctJUXihFqXJ91hjq5iqD48dpi7116BderW0sRv0ljePnF2Dh222ZPiH3jwwm4guKbdT5y86YKFqX60FE9KyVSUehsw40rIgTvFyksZl9d9HOTVQgkNn+jqWbanQ3HFKE9Ea1u6pAw2cO2efO3dHbJev6Nh
        aws-key
ssh_pwauth: false
disable_root: false
package_update: true
packages:
  - apache2
  - php
  - libapache2-mod-php
runcmd:
  - sudo systemctl restart apache2
write_files:
  - path: /var/www/html/image.php
    content: >
      	<?php $ihrname = "Jasmin Jeyakumar"; ?>
        <html>
        <head>
        <title><?php echo($ihrname) ?></title>
        </head>
        <body>
               New York city.
        <br />
     <img src="https://kn04-jasminjeyakumar.s3.amazonaws.com/newYork2023.jpg" />

        </body>
        </html>
    permissions: "0666"



  <img src="https://kn04-jasminjeyakumar.s3.amazonaws.com/newYork2023.jpg" />
```
- Screenshot der Seite image.php (mit sichtbarer URL)
![image](https://github.com/xmin12/m346_Jasmin.jeya/assets/112725311/a7e4fd5d-0d40-431c-b686-57c515272ad7)

## C) Elastic Block Storage (EBS) hinzufügen
![image](https://github.com/xmin12/m346_Jasmin.jeya/assets/112725311/c484655a-c7b6-49e2-ae2f-18f13ecb0a4f)

## D) Speichereigenschaften erkennen
|             | Typ         | Persistenz    |
| :---        |    :----:   |          ---: |
|EBS          | hot         | nein          |
|EBS 2nd Vol  | hot         | ja            |
|S3           | warm        | ja            |


Das EBS-Root-Volume ist "hot", da es den Webserver hostet und die Datei "image.php" ständig zur Verfügung stellen muss. Allerdings ist es nicht persistent, da die Dateien nach dem Herunterfahren der Instanz gelöscht werden.

Das EBS-Zweitvolume ist "cold", da es keine kontinuierliche Bereitstellung von Daten erfordert. Es ist jedoch persistent, da die Daten nach dem Herunterfahren der Instanz nicht gelöscht werden.

S3 ist "hot", da es das Bild für die "image.php"-Datei bereitstellt und persistent ist, da die Daten auch nach dem Herunterfahren der Instanz nicht gelöscht werden.
