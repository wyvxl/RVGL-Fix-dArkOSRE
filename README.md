# RVGL Fix for dArkOSRE (Debian Trixie) - R36S

[English version below](#english-version)

---

Este repositorio contiene los archivos y configuraciones necesarias para solucionar los problemas de compatibilidad y dependencias de RVGL (Re-Volt) en la consola R36S utilizando el sistema operativo dArkOSRE (basado en Debian 13 Trixie, arquitectura aarch64).

## Instalación

Debido a que dArkOSRE está basado en Debian Trixie, algunas librerías han cambiado de versión. Para que el juego funcione correctamente y encuentre las librerías esperadas, debes crear los siguientes enlaces simbólicos (symlinks) accediendo a la consola vía SSH:

```bash
sudo ln -s /usr/lib/aarch64-linux-gnu/libunistring.so.5 /usr/lib/aarch64-linux-gnu/libunistring.so.2
sudo ln -s /usr/lib/aarch64-linux-gnu/libenet.so.7 /usr/lib/aarch64-linux-gnu/libenet.so.2
sudo ln -s /usr/lib/aarch64-linux-gnu/libFLAC.so.12 /usr/lib/aarch64-linux-gnu/libFLAC.so.8
```

## Fix de Video (OpenGL)

Este repositorio ya incluye el archivo `profiles/rvgl.ini` pre-configurado para evitar el error "Failed to load OpenGL functions". Los ajustes clave aplicados son:
- `VideoBackend = "GL"`
- `Shaders = 1`

Esto asegura que el juego utilice el driver correcto para dArkOSRE.

## Permisos

Asegúrate de que los archivos ejecutables tengan los permisos correctos antes de intentar lanzar el juego desde PortMaster. Ejecuta los siguientes comandos vía SSH o en la terminal, dentro de la carpeta donde ubicaste el juego:

```bash
chmod +x RVGL.sh
chmod +x rvgl.arm64
```

## Créditos

Solución técnica desarrollada por Leandro Lizano (comunidad R36S).

---

<a name="english-version"></a>

# English Version

This repository contains the necessary files and configurations to solve compatibility and dependency issues for RVGL (Re-Volt) on the R36S console using the dArkOSRE operating system (based on Debian 13 Trixie, aarch64 architecture).

## Installation

Since dArkOSRE is based on Debian Trixie, some library versions have changed. To ensure the game runs correctly and finds the expected libraries, you must create the following symbolic links (symlinks) via SSH:

```bash
sudo ln -s /usr/lib/aarch64-linux-gnu/libunistring.so.5 /usr/lib/aarch64-linux-gnu/libunistring.so.2
sudo ln -s /usr/lib/aarch64-linux-gnu/libenet.so.7 /usr/lib/aarch64-linux-gnu/libenet.so.2
sudo ln -s /usr/lib/aarch64-linux-gnu/libFLAC.so.12 /usr/lib/aarch64-linux-gnu/libFLAC.so.8
```

## Video Fix (OpenGL)

This repository already includes the pre-configured `profiles/rvgl.ini` file to prevent the "Failed to load OpenGL functions" error. The key settings applied are:
- `VideoBackend = "GL"`
- `Shaders = 1`

This ensures the game uses the correct driver for dArkOSRE.

## Permissions

Make sure the executable files have the correct permissions before attempting to launch the game from PortMaster. Run the following commands via SSH or in the terminal, inside the folder where you placed the game:

```bash
chmod +x RVGL.sh
chmod +x rvgl.arm64
```

## Credits

Technical solution developed by Leandro Lizano (R36S community).
