
# Comunicación FPT
#
__*Los siguientes scripts están hechos en Python y están enfocados al escaneo de puertos mediante sentencias que nos proporcionaran algunos comandos para analizar información de la red y escanear los puertos que tenemos abiertos y cerrados en nuestro equipo.*__

### 1. Script en Python unicamente para establecer la conexión FTP
#
```bash
#
# Script para transferencia de FTP
# Objetivo: Conectarse a servidor ftp y hacer un upload de un archivo.
# Eri9ck Danel Blanco de la Garza
#
# Importando modulo ftp
from ftplib import FTP
#
# Estableciendo conexión a servidor
#
ftp = FTP ('<Aquí va ti IP>')
#
#
```

### 2. Vizualizando la conexión con el servidor desde Wireshark

![puer](/FILES/cont/wire.png "puertos$servicios")
#

### 3. Haaciendo un cat al archivo que se transfirió desde la otra maquina. 
![puer](/FILES/cont/final.png "puertos$servicios")
#

[Subir](#top)