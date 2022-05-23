# Installation

Installer `docker` et `docker-compose`

Sur Debian & Ubuntu:
```bash
sudo apt install docker docker-compose
```

Sur ArchLinux:
```bash
sudo pacman -S docker docker-compose
```

Vous pouvez également installer `git` et faire `git clone https://github.com/Kaniville/docker-wordpress` pour le télecharger.

Si vous avez décider de télecharger le fichier zip, un simple `unzip NOM_DU_ZIP.zip` dans le répertoire ou il a été télecharger suffit à le décompresser.

# Configuration

Dans le repertoire du serveur, entrer la commande `sudo docker-compose up -d`.

Puis entrez cette commande afin de rendre accessible le dossier "wp-content" à docker:
```
# docker exec -ti WORDPRESS_CONTAINER_NAME sh -c "chown -R www-data:www-data wp-content"
```

Exemple:
```
# docker exec -ti docker-wordpress-wordpress-1 sh -c "chown -R www-data:www-data wp-content"

```

Enfin creez la base de donnée `wordpress` depuis votre `localhost:8080`, et voila, configurez Wordpress et tout est bon !

- Pour eteindre le serveur, faire `sudo docker-compose stop`

- Pour voir les infos des containers, faire `sudo docker-compose ps`

- PHP-MY-ADMIN se situe au localhost au port `:8080` (`localhost:8080`)

- Pour accéder à la ligne de commande de mariadb (mysql), faire:
```
sudo docker exec -ti docker-wordpress-mariadb-1 mysql -u root -p
```
<sub>Ici, `docker-wordpress-mariadb-1` est le nom du container mariadb (mysql)</sup>

<hr>

```
.                                <--Lancer le serveur depuis ici
├── config
│   └── mysql
│       └── my.cnf
├── docker-compose.yml
├── README.md
```
<sub>Repertoire du serveur Wordpress</sub>

- Pour afficher les infos des images/containers docker, `sudo docker images` & `sudo docker container ps`

- Pour supprimer toutes les images docker inutilisées, `sudo docker image prune`

- Pour supprimer tout les containers inutilisés, `sudo docker container prune`

- Pour supprimer une seule image ou un seul container, remplacez `prune` par `rm CONTAINER_ID`
