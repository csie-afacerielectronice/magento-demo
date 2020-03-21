# Instalare Magento folosind Docker

Demonstratia a fost realizata pe o masina virtuala cu 4gb RAM si 2 CPU pe sistemul de operare Ubuntu 18.04

## Instalare docker si docker-compose

```
sudo apt update
sudo apt install apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"
sudo apt update
sudo apt install docker-ce
docker --version
```

```
sudo curl -L https://github.com/docker/compose/releases/download/1.25.4/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
docker-compose --version
```

## Instalare Magento 2

```
mkdir magento
cd magento
curl -sSL https://raw.githubusercontent.com/bitnami/bitnami-docker-magento/master/docker-compose.yml > docker-compose.yml
mkdir ./mariadb_data ./magento_data ./elasticsearch_data
chmod -R 777 ./mariadb_data ./magento_data ./elasticsearch_data
sudo sysctl -w vm.max_map_count=262144
```

Pentru ca Magento sa fie accesibil de pe IP-ul public adaugati in docker-compose.yml adresa MAGENTO_HOST

```
docker-compose up -d
```

In cazul in intampinati dificultati cu setarea MAGENTO_HOST urmariti instructiunile de aici https://github.com/bitnami/bitnami-docker-magento/issues/85#issuecomment-418826319

## Credentialele pentru sectiunea de admin

```
user:bitnami1
```

# Referinte

https://hub.docker.com/r/bitnami/magento/

https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-18-04

https://www.digitalocean.com/community/tutorials/how-to-install-docker-compose-on-ubuntu-18-04

