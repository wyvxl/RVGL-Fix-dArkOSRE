# RVGL Fix for dArkOSRE (Debian Trixie) - R36S

Este repositorio contiene los archivos y configuraciones necesarias para solucionar los problemas de compatibilidad y dependencias de RVGL (Re-Volt) en la consola R36S utilizando el sistema operativo dArkOSRE (basado en Debian 13 Trixie, arquitectura aarch64).

## Instalación

Debido a que dArkOSRE está basado en Debian Trixie, algunas librerías han cambiado de versión. Para que el juego funcione correctamente y encuentre las librerías esperadas, debes crear los siguientes enlaces simbólicos (symlinks) accediendo a la consola vía SSH:

```bash
sudo ln -s /usr/lib/aarch64-linux-gnu/libunistring.so.5 /usr/lib/aarch64-linux-gnu/libunistring.so.2
sudo ln -s /usr/lib/aarch64-linux-gnu/libenet.so.7 /usr/lib/aarch64-linux-gnu/libenet.so.2
sudo ln -s /usr/lib/aarch64-linux-gnu/libFLAC.so.12 /usr/lib/aarch64-linux-gnu/libFLAC.so.8
```

## Permisos

Asegúrate de que los archivos ejecutables tengan los permisos correctos antes de intentar lanzar el juego desde PortMaster. Ejecuta los siguientes comandos vía SSH o en la terminal, dentro de la carpeta donde ubicaste el juego:

```bash
chmod +x RVGL.sh
chmod +x rvgl.arm64
```

## Fix de Video (OpenGL)

Este repositorio ya incluye el archivo `profiles/rvgl.ini` pre-configurado para evitar el error "Failed to load OpenGL functions". Los ajustes clave aplicados son:
- `VideoBackend = "GL"`
- `Shaders = 1`

Esto asegura que el juego utilice el driver correcto para dArkOSRE.

## Créditos

Solución técnica desarrollada por Leandro Lizano (comunidad R36S).
