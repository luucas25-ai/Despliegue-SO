# Despliegue-SO

Instalación y configuración de Ubuntu en VirtualBox.

Realizado por Francisco, Roberto y Lucas.

## 1. Creación de la máquina virtual

Creamos la máquina y le asignamos la ISO de Ubuntu.

![Asignación de la ISO](img/Asignacion-de-Imagen-ISO.png)

Asignamos la RAM, la CPU y el disco.

![Asignación de RAM](img/Asignacion-de-RAM.png)

## 2. Arranque

Ponemos la unidad óptica primero en el orden de arranque.

![Orden de arranque](img/Orden-de-arranque.png)

Comprobamos que la ISO y el disco están conectados.

![Almacenamiento](img/Comprobacion-de-almacenamiento.png)

## 3. Instalación de Ubuntu

Elegimos el idioma.

![Idioma](img/Idioma.png)

Elegimos borrar el disco e instalar Ubuntu.

![Configuración del disco](img/Configuración-del-disco.png)

Creamos el usuario con una contraseña segura.

![Contraseña segura](img/Contrasenna-segura.png)

Revisamos el resumen e instalamos.

![Instalación](img/Instalacion.png)

## 4. Guest Additions

Insertamos el CD de las Guest Additions.

![Guest Additions](img/Instalacion-de-guest-additions.png)

Actualizamos la lista de paquetes.

```bash
sudo apt update
```

![Primer paso](img/Primer-paso-guest.png)

Instalamos las herramientas necesarias.

```bash
sudo apt install build-essential dkms linux-headers-$(uname -r)
```

![Segundo paso](img/Segundo-paso-guest.png)

Ejecutamos el instalador y reiniciamos.

```bash
sudo ./VBoxLinuxAdditions.run
```

![Tercer paso](img/Tercer-paso.png)

Activamos el portapapeles bidireccional.

![Portapapeles bidireccional](img/Portapapeles%20a%20bidireccional.png)

Activamos la pantalla dinámica.

![Pantalla dinámica](img/Pantalla%20dinamica.png)

## 5. Carpeta compartida

Añadimos la carpeta compartida en VirtualBox.

![Carpeta compartida](img/Carpeta%20compartida.png)

Añadimos el usuario al grupo `vboxsf`.

```bash
sudo usermod -aG vboxsf $USER
```

![Añadir usuario al grupo](img/Añadir%20usu%20al%20grupo%20de%20virtual.png)

Comprobamos que funciona.

![Verificación](img/Verificacion%20de%20carpeta%20compartida.png)

## 6. Segundo disco

Creamos un disco VDI de 15 GB.

![VDI 15 GB](img/VDI%2015gb.png)

Identificamos el disco.

```bash
lsblk
```

![Identificación de disco](img/Identificacion%20de%20disco.png)

Creamos las particiones con `parted`.

![Creación de particiones](img/Creacion%20de%20particion%20de%20disco.png)

Mostramos el disco sobre el que trabajamos.

![Disco de trabajo](img/Muestra%20sobre%20lo%20que%20estamos%20trabajando.png)

Formateamos en FAT32.

```bash
sudo mkfs.vfat -F 32 /dev/sdb
```

![Formateo en FAT32](img/Formateo%20de%20particion%20en%20fat32.png)

Mostramos el disco con su formato.

```bash
lsblk -f /dev/sdb
```

![Discos y formatos](img/Muestra%20de%20discos%20junto%20con%20sus%20formatos.png)

## 7. Actualización del sistema

Actualizamos la lista de paquetes.

```bash
sudo apt update
```

![Lista de paquetes](img/Actualiza%20la%20lista%20de%20paquetes.png)

Vemos los paquetes con una versión más nueva.

```bash
apt list --upgradable
```

![Paquetes actualizables](img/muestra%20de%20paquetes%20instalados%20con%20version%20mas%20nueva%20disponible.png)

Instalamos las actualizaciones.

```bash
sudo apt upgrade
```

![Instalación de actualizaciones](img/instalacion%20de%20las%20actualizaciones.png)
