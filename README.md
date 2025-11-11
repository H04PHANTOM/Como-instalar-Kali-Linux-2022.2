# Como-instalar-Kali-Linux-2022.2
Este repo es una guia de instalacion de Kali Linux 2022.2 la cual es una Version de Kali muy estable 

# 🐉 Instalación de Kali Linux 2022.2
![Kali Linux Logo](./kali-linux.png)
<!-- Reemplaza ./kali-linux.png con la ruta de tu imagen o un enlace directo -->
Este documento detalla el procedimiento para instalar y configurar **Kali Linux 2022.2**, asegurando compatibilidad y estabilidad con el kernel **5.16**.
> ⚠️ **Importante:** Sigue los pasos exactamente en el orden indicado para evitar errores durante la instalación.
---
## 📥 Paso 1: Ingresar al enlace de descarga
Abre el siguiente enlace para acceder a las imágenes de instalación de Kali Linux 2022.2:
https://old.kali.org/kali-images/kali-2022.2/

yaml
Copiar código
---
## 🧩 Paso 2: Editar el archivo `sources.list`
Abre el archivo de fuentes con el siguiente comando:
```bash
sudo nano /etc/apt/sources.list
Agrega la siguiente URL adicional al final del archivo:

arduino
Copiar código
https://mirrors.ocf.berkeley.edu/kali/
Guarda los cambios y cierra el editor (Ctrl + O, luego Ctrl + X).
🔑 Paso 3: Actualizar claves de Linux
Instala el paquete dirmngr:

bash
Copiar código
sudo apt install -y dirmngr
🗂️ Paso 4: Crear las carpetas necesarias para GPG
Crea la carpeta para las claves GPG:

bash
Copiar código
sudo mkdir -p /root/.gnupg
sudo chmod 700 /root/.gnupg
Crea también el directorio actualizado para las claves de confianza:

bash
Copiar código
sudo mkdir -p /etc/apt/trusted.gpg.d
🔐 Paso 5: Actualizar las claves GPG
Ejecuta el siguiente comando para importar las claves del repositorio:

bash
Copiar código
sudo gpg --no-default-keyring --keyring /etc/apt/trusted.gpg.d/kali-archive-keyring.gpg --keyserver keyserver.ubuntu.com --recv-keys ED65462EC8D5E4C5
Nota: Asegúrate de escribir los guiones dobles (--) correctamente, ya que son esenciales para el comando.

♻️ Paso 6: Actualizar e instalar dependencias
Actualiza el sistema y las dependencias principales:

bash
Copiar código
sudo apt update
sudo apt upgrade -y
sudo apt install -y perl
sudo apt upgrade -y
sudo apt autoremove
⚙️ Paso 7: Instalar dependencias del kernel 5.16
Accede al siguiente enlace:

arduino
Copiar código
http://old.kali.org/kali/pool/main/l/linux/
Busca y descarga el paquete correspondiente:

Copiar código
linux-headers-5.16.0-kali7
🧱 Paso 8: Fijar el kernel y GRUB a la versión 5.16
Edita el archivo del GRUB:

bash
Copiar código
sudo nano /etc/default/grub
Modifica (o agrega) la siguiente línea:

bash
Copiar código
GRUB_DEFAULT="1>2"
Guarda los cambios y ejecuta:

bash
Copiar código
sudo update-grub
✅ Instalación completada
Tu sistema Kali Linux 2022.2 está ahora configurado con el kernel 5.16 y las claves actualizadas correctamente.
📸 Sugerencia
Puedes añadir aquí una captura de pantalla de tu sistema una vez finalizada la instalación:

scss
Copiar código
![Instalación completa](./instalacion-finalizada.png)
💬 Autor
Creado por [Tu Nombre o Alias]
💻 Proyecto alojado en GitHub
Copiar código
