# Dataiku en Docker

## Instalación de Docker

```bash
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

# Add the repository to Apt sources:
echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update

# Install Docker
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# Verify docker group exists
sudo groupadd docker

# Add your user to the docker group
sudo usermod -aG docker $USER

# Log out and log back in so that your group membership is re-evaluated
newgrp docker
```

## Verificar la instalación de Docker

```bash
docker run hello-world
```

## Correr Dataiku en Docker

> [!WARNING]
> Estos contenedores no tienen volumenes, es decir, si se borra el contenedor se borra todo lo que haya dentro. Para evitar esto, se pueden crear volumenes y montarlos en el contenedor.

### Creando la imagen de Dataiku a partir del Dockerfile

```bash
wget https://raw.githubusercontent.com/Xabierland/SAD/main/INSTALACIONES/Docker/dockerfile
docker build -t dataiku-dss-11.3.2 .
docker run -p 11000:11000 -dit --restart unless-stopped --name dataiku dataiku-dss-11.3.2

```

### Usando MI imagen de Dataiku de Docker Hub

```bash
docker run -p 11000:11000 -dit --restart unless-stopped --name dataiku xabierland/dataiku-dss-11.3.2
```
