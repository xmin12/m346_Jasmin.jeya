# KN05: Netzwerk / Sicherheit

## A) Diagramm erstellen
Diagramm über Netzwerke gezeichnet
![image](https://github.com/xmin12/m346_Jasmin.jeya/assets/112725311/1f264d7e-99e9-4fc8-956c-221c5bc2529f)

## B) Subnetz und private IP wählen
![image](https://github.com/xmin12/m346_Jasmin.jeya/assets/112725311/6742dd0b-f4c3-4ebd-82b0-b401918f43ca)
1. 172.31.80.0/20
2. 172.31.48.0/20

## C) Objekte und Instanzen erstellt
- Liste der Sicherheitsgruppe mit sprechenden Namen/Feldern:
![image](https://github.com/xmin12/m346_Jasmin.jeya/assets/112725311/049607d5-17a0-498b-8902-0080585c0481)
- Inbound-Regel für die DB-Sicherheitsgruppe:
![image](https://github.com/xmin12/m346_Jasmin.jeya/assets/112725311/171f6269-8ad9-4a73-bcc0-c05045191b4e)
- Liste der Elastic IPs mit sprechenden Namen:
![image](https://github.com/xmin12/m346_Jasmin.jeya/assets/112725311/46897fe6-0bd9-484c-a717-c5f1e3afd6a1)
> index.html
![image](https://github.com/xmin12/m346_Jasmin.jeya/assets/112725311/785261ef-3ec5-47ed-b066-83e89f76da7b)
> info.php
![image](https://github.com/xmin12/m346_Jasmin.jeya/assets/112725311/cb4517a6-4a1e-4ca9-9198-b308b1558faa)
> db.php
![image](https://github.com/xmin12/m346_Jasmin.jeya/assets/112725311/e9bc5f98-b2b0-4497-abd1-58b5a8a57a29)
- Die  beide gestoppt Instanzen:
![image](https://github.com/xmin12/m346_Jasmin.jeya/assets/112725311/6fa21de7-0bf6-466c-9ced-570fb2aee54f)
- Details beider Instanzen so dass die Subnet ID
![image](https://github.com/xmin12/m346_Jasmin.jeya/assets/112725311/f3f83205-e660-47d8-8669-b76bfb5dfa07)
![image](https://github.com/xmin12/m346_Jasmin.jeya/assets/112725311/f9fb8f9b-36d5-4d49-862b-b9b08d61983f)
### Web-config.yaml
```YAML
#cloud-config

# Users Configuration
users:
  - name: ubuntu
    sudo: ALL=(ALL) NOPASSWD:ALL
    groups: users, admin
    home: /home/ubuntu
    shell: /bin/bash
    ssh_authorized_keys:
      - ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDcb7reFZ0ycalWUpfU2uzOBY2AYqy9tLgEbhKIj9XMjie8NSw9Mx++3hAaQyY1ydKNyFFnKMU9/PO2qRv3jMqJbQ0eMOSDBQ6yIXIIy+Y/BHG37HD4Aa5RSGomrBA8XrHnSUI0ReX0L1/hJ/2kZA7vlKe4DDRA5GhOW5G4MQmUQJqvcx6x6Yl6JSX0/N27clTUNlYzszYnqwB7okMORRPQveyVmGg3P7TlGo79O8tXnG/ZIKs7XjwqJvngo2DkcNegoSW6gUAwc9YAEAvyRgIBgydCme3/6m5tFbSQaU64q2Vd/x0HMFAhEaclR4LbRa2NNhkvF70pncWQH90rufOv aws-key
      - ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC0WGP1EZykEtv5YGC9nMiPFW3U3DmZNzKFO5nEu6uozEHh4jLZzPNHSrfFTuQ2GnRDSt+XbOtTLdcj26+iPNiFoFha42aCIzYjt6V8Z+SQ9pzF4jPPzxwXfDdkEWylgoNnZ+4MG1lNFqa8aO7F62tX0Yj5khjC0Bs7Mb2cHLx1XZaxJV6qSaulDuBbLYe8QUZXkMc7wmob3PM0kflfolR3LE7LResIHWa4j4FL6r5cQmFlDU2BDPpKMFMGUfRSFiUtaWBNXFOWHQBC2+uKmuMPYP4vJC9sBgqMvPN/X2KyemqdMvdKXnCfrzadHuSSJYEzD64Cve5Zl9yVvY4AqyBD aws-key
    ssh_pwauth: false
    disable_root: false

# Package Configuration
package_update: true
packages:
  - apache2
  - curl
  - wget
  - php
  - libapache2-mod-php
  - php-mysql
  - adminer

# Run Commands
runcmd:
  - sudo a2enconf adminer
  - sudo systemctl restart apache2

# Write Files
write_files:
  - content: |
      <?php
      $servername = "172.31.2.0";
      $username = "admin";
      $password = "password";
      $dbname = "mysql";
      // Create connection
      $conn = new mysqli($servername, $username, $password, $dbname);
      // Check connection
      if ($conn->connect_error) {
        die("Connection failed: " . $conn->connect_error);
      }
      $sql = "SELECT Host, User FROM mysql.user;";
      $result = $conn->query($sql);
      while ($row = $result->fetch_assoc()) {
        echo ($row["Host"] . " / " . $row["User"] . "<br />");
      }
    path: /var/www/html/db.php
    permissions: "0644"
    owner: root:root

  - content: |
      <?php
      phpinfo();
    path: /var/www/html/info.php
    permissions: "0644"
    owner: root:root

```
### db-config.yaml
```YAML

#cloud-config

users:
  - name: ubuntu
    sudo: ALL=(ALL) NOPASSWD:ALL
    groups: users, admin
    home: /home/ubuntu
    shell: /bin/bash
    ssh_authorized_keys:
      - ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDcb7reFZ0ycalWUpfU2uzOBY2AYqy9tLgEbhKIj9XMjie8NSw9Mx++3hAaQyY1ydKNyFFnKMU9/PO2qRv3jMqJbQ0eMOSDBQ6yIXIIy+Y/BHG37HD4Aa5RSGomrBA8XrHnSUI0ReX0L1/hJ/2kZA7vlKe4DDRA5GhOW5G4MQmUQJqvcx6x6Yl6JSX0/N27clTUNlYzszYnqwB7okMORRPQveyVmGg3P7TlGo79O8tXnG/ZIKs7XjwqJvngo2DkcNegoSW6gUAwc9YAEAvyRgIBgydCme3/6m5tFbSQaU64q2Vd/x0HMFAhEaclR4LbRa2NNhkvF70pncWQH90rufOv aws-key
      - ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC0WGP1EZykEtv5YGC9nMiPFW3U3DmZNzKFO5nEu6uozEHh4jLZzPNHSrfFTuQ2GnRDSt+XbOtTLdcj26+iPNiFoFha42aCIzYjt6V8Z+SQ9pzF4jPPzxwXfDdkEWylgoNnZ+4MG1lNFqa8aO7F62tX0Yj5khjC0Bs7Mb2cHLx1XZaxJV6qSaulDuBbLYe8QUZXkMc7wmob3PM0kflfolR3LE7LResIHWa4j4FL6r5cQmFlDU2BDPpKMFMGUfRSFiUtaWBNXFOWHQBC2+uKmuMPYP4vJC9sBgqMvPN/X2KyemqdMvdKXnCfrzadHuSSJYEzD64Cve5Zl9yVvY4AqyBD aws-key
    ssh_pwauth: false
    disable_root: false

package_update: true
packages:
  - mariadb-server

runcmd:
  - sudo mysql -sfu root -e "GRANT ALL ON *.* TO 'admin'@'%' IDENTIFIED BY 'password' WITH GRANT OPTION;"
  - sudo sed -i 's/127.0.0.1/0.0.0.0/g' /etc/mysql/mariadb.conf.d/50-server.cnf
  - sudo systemctl restart mariadb.service
```
