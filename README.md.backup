
## About
This will install OSTicket V1.16.3 on k3s cluster - An open source helpdesk / ticketing system
## Maintainer

- Mohamed zakaria
 ------
## Prerequisites :
 - K3s 
 - Docker
 - MetaLB

## Installation
### 1. MySQL :
- Create Directory on localhost  /mnt/data to mount database volume
- Create PersistentVolume run the following 
```
kubectl create -f mysql-pv-pvc.yaml
```
- Ensure you have store the essential data for MySQL Database by editing the ConfigMap file
```
apiVersion: v1
kind: ConfigMap
metadata:
  name: osticket-mysql-mysecret
data:
   MYSQL_ROOT_PASSWORD: secret
   MYSQL_DATABASE: osticket
   MYSQL_USER: osticket
   MYSQL_PASSWORD: secret
```
After modification run the file
```
kubectl create -f ConfigMap.yaml
```
- Deploy the mysql service using mysql:5.6 image by the following command
```
kubectl create -f mysql.yaml
```

### 2. OSTicket:
- Create Directory on localhost  /mnt/html to mount osticket volume
- Deploy the OSTicket service using official image osticket/osticket:latest  by the following command
```
kubectl create -f ost.yaml
```

Wait for the installation to complete and get  then browse to your osTicket staff control panel at 
`http://localhost:8080/scp/`. Login with default admin user & password:

* username: **ostadmin**
* password: **Admin1**
## Quick Start
1. 
Ensure you have a MySQL 5 container running that osTicket can use to store its data.

```bash
docker run -d \
    -e MYSQL_ROOT_PASSWORD=secret \
    -e MYSQL_USER=osticket \
    -e MYSQL_PASSWORD=secret \
    -e MYSQL_DATABASE=osticket \
    --name osticket_mysql\
    mysql:5
```

Now run this image and link the MySQL container.

```bash
docker run -d --name osticket --link osticket_mysql:mysql -p 8080:80 devinsolutions/osticket
```

Wait for the installation to complete then get EXTERNAL-IP for service/osticket then  browse to your osTicket staff control panel at
`http://EXTERNAL-IP:8080/scp/`. Login with default admin user & password:

* username: **ostadmin**
* password: **Admin1**

