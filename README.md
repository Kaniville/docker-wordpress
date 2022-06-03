# Installation

Install `docker` & `docker-compose`

Debian & Ubuntu:
```bash
# apt install docker docker-compose
```

ArchLinux:
```bash
# pacman -S docker docker-compose
```

You can clone the repository with `git` (`git clone https://github.com/Kaniville/docker-wordpress`).

You can also download a ZIP file from the Github UI and unzip it with `unzip NAME_OF_FILE.zip`

# Configuration

Use the command `# docker-compose up -d` (with root privileges) from the "docker-wordpress" directory to start the Wordpress Server.

Enter this command to enter inside the Wordpress Container
```
# docker-compose exec wordpress bash
```

From here, we need to change permissions to let us edit and create files
```
cd ..
umask 0007 html
find html -type d -exec sudo chmod 775 {} +
find html -type f -exec sudo chmod 664 {} +
```

# Commands

- Start the server: `# docker-compose start`

- Stop the server: `# docker-compose stop`

- Show containers informations: `# docker-compose ps`

- Show logs from a container: `# docker-compose logs CONTAINER_NAME`

- Delete container(s): `# docker-compose rm CONTAINER_NAME` or without the container name

# Informations

- Phpmyadmin is at "localhost:8080"

- To access the mariadb console, enter:
```
# docker-compose exec MARIADB_CONTAINER_NAME mysql -u root -p
```

```
.                   <-- Start the server from here
├── config
│   └── mysql
│       └── my.cnf
├── wp-content
│   └── ...
├── docker-compose.yml
├── README.md

```
<sub>Directory of the Wordpress server</sub>
