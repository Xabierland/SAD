# Instalación de Anaconda y Dataiku

> [!NOTE]
> Distro: Debian 12 (Bookworm)

## Anaconda

### Descargar Anaconda

```bash
sudo apt-get install libgl1-mesa-glx libegl1-mesa libxrandr2 libxrandr2 libxss1 libxcursor1 libxcomposite1 libasound2 libxi6 libxtst6
wget https://repo.anaconda.com/archive/Anaconda3-2023.09-0-Linux-x86_64.sh
sudo chmod +x Anaconda3-2023.09-0-Linux-x86_64.sh
```

### Instalar Anaconda

```bash
./Anaconda3-2023.09-0-Linux-x86_64.sh
```

### Configurar Anaconda

```bash
source anaconda3/bin/activate
conda init # Puede ser necesario indicar la SHELL e incluso reiniciar la terminal
conda config --set auto_activate_base False
```

### Crear entorno virtual

```bash
conda create -n sad python=3.8
```

### Activar entorno virtual

```bash
conda activate SAD
```

### Instalar GUI

```bash
conda install anaconda-navigator
```

### Ejecutar GUI

```bash
anaconda-navigator
```

### Desactivar entorno virtual

```bash
conda deactivate
```

## Dataiku

> [!CAUTION]
> Solo he conseguido que funcione en Debian 12 mediante contenedores. En mi caso he usado **distrobox** para crear un contenedor con Ubuntu:22.04 mediante **distrobox create --name Ubuntu --image ubuntu:22.04**. Una vez creado el contenedor, entrar con **distrobox enter Ubuntu** y seguir los pasos de la instalación.


### Descargar Dataiku

```bash
wget https://cdn.downloads.dataiku.com/public/dss/11.3.2/dataiku-dss-11.3.2.tar.gz
tar xzf dataiku-dss-11.3.2.tar.gz
```

### Instalar Dataiku

```bash
mkdir $HOME/.dataiku
mv dataiku-dss-11.3.2 $HOME/.dataiku-dss-11.3.2
sudo -i "$HOME/.dataiku-dss-11.3.2/scripts/install/install-deps.sh"
.$HOME/.dataiku-dss-11.3.2/installer.sh -d $HOME/.dataiku -p 11000
```

### Ejecutar Dataiku

```bash
./.dataiku/bin/dss start
```

### Acceder a Dataiku

```bash
http://localhost:11000
```
