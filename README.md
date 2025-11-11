# Como-instalar-Kali-Linux-2022.2
Este repo es una guia de instalacion de **Kali Linux 2022.2** asegurando compatibilidad y estabilidad con el kernel **5.16**.
> ⚠️ **Importante:** Sigue los pasos exactamente en el orden indicado para evitar errores durante la instalación.
---
## 📥 Fase 1: Descarga la ISO de Kali Linux 2022.2 y Descarga Virtual Box

Primero Instala Virtual Box de su fuente oficial 
```bash
https://www.virtualbox.org/
```
Abre el siguiente enlace para acceder a las imágenes de instalación de Kali Linux 2022.2
Selecciona el que dice (**kali-linux-2022.2-installer-amd64.iso**):
```bash
https://old.kali.org/kali-images/kali-2022.2/
```
---
# Ya que tengas iniciada tu maquina virtual ya con linux funcionando puedes continuar con lo siguiente
# Configuracion inicial de **Kali Linux 2022.2**

# 🧩 Paso 1: Editar el archivo `sources.list`
Abre el archivo de fuentes con el siguiente comando:
```bash
sudo nano /etc/apt/sources.list
```
Agrega la siguiente URL adicional al final del archivo:
```bash
https://mirrors.ocf.berkeley.edu/kali/ kali-rolling main contrib non-free
```
Guarda los cambios y cierra el editor (Ctrl + O, luego Ctrl + X).

🔑 Paso 2: Actualizar claves de Linux
Instala el paquete dirmngr:
```bash
sudo apt install -y dirmngr
```
🗂️ Paso 3: Crear las carpetas necesarias para GPG
Crea la carpeta para las claves GPG:
```bash
sudo mkdir -p /root/.gnupg
sudo chmod 700 /root/.gnupg
```
Crea también el directorio actualizado para las claves de confianza:
```bash
sudo mkdir -p /etc/apt/trusted.gpg.d
```
🔐 Paso 4: Actualizar las claves GPG
Ejecuta el siguiente comando para importar las claves del repositorio:
```bash
sudo gpg --no-default-keyring --keyring /etc/apt/trusted.gpg.d/kali-archive-keyring.gpg --keyserver keyserver.ubuntu.com --recv-keys ED65462EC8D5E4C5
```
Nota: Asegúrate de escribir los guiones dobles (--) correctamente, ya que son esenciales para el comando.

♻️ Paso 5: Actualizar e instalar dependencias
Actualiza el sistema y las dependencias principales:
Nota: Ejecuta cada comando uno por uno, asi evitas que el sistema se corrompa
```bash
sudo apt update && sudo apt upgrade -y
sudo apt install -y perl
sudo apt upgrade -y
sudo apt autoremove
```
⚙️ Paso 6: Instalar dependencias del kernel 5.16
Accede al siguiente enlace:
```bash
http://old.kali.org/kali/pool/main/l/linux/
```
Busca y descarga los siguientes paquetes:
```bash
linux-headers-5.16.0-kali7-amd64_5.16.18-1kali1_amd64.deb
linux-headers-5.16.0-kali7-common_5.16.18-1kali1_all.deb
linux-kbuild-5.16_5.16.18-1kali1_amd64.deb
linux-compiler-gcc-11-x86_5.15.15-2kali1_amd64.deb
```
🧱 Paso 7: Fijar el kernel y GRUB a la versión 5.16
Edita el archivo del GRUB:
```bash
sudo nano /etc/default/grub
```
Modifica (o agrega) la siguiente línea:
```bash
GRUB_DEFAULT="1>2"
```
Guarda los cambios y ejecuta:
```bash
sudo update-grub
```
✅ Instalación completada
Tu sistema Kali Linux 2022.2 está ahora configurado con el kernel 5.16 y las claves actualizadas correctamente.
