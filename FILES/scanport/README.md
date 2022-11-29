
# Escáner de puertos

---
#
__*Los siguientes scripts están hechos en Python y están enfocados al escaneo de puertos mediante potentes herramientas en sus comandos para analizar información de la red..*__

### 1. Script en Python para escanear puertos indicando primero nuestra ip y despues el rango de puertos que va a escanear el script
#
```python
#Erick Daniel Blanco de la Garza
#Matricula: 1756734
#Parte 1
#Importamos librerias necesarias
import sys
from socket import *
#Parte 2
#Mode de ejecución del script
#port_scan.py <host> <start_port>-<end-port>
#Segundo argumento se guarda en vatiable portstrs
host = sys.argv[1]
portstrs = sys.argv[2].split('-')
#Parte 3
#portstrs contiene dos valores que asignamos
#en start_port el valor de inicio
#en end_port el valor final
start_port = int(portstrs[0])
end_port = int(portstrs[1])
#Parte 4
#Para usar en el socket asignamos lo de la
#variable host a target_ip
#Definimos una lista de puertos opened_ports
target_ip = gethostbyname (host)
opened_ports = []
#Parte 5
#Iniciamos el bucle for para probar puertos
for port in range(start_port, end_port):
        sock = socket(AF_INET, SOCK_STREAM)
        sock.settimeout(10)
        result = sock.connect_ex((target_ip, port))
        if result == 0:
                opened_ports.append(port)
#Parte 6
# Se imprime salida
print('Opened ports: ')
#
for i in opened_ports:
        print()
```
![scaner](/FILES/cont/sp1.png "port_scanv1.py")
#
---

### 2. scan_portv2
#### Script Python para revisar los puertos dentro de de un rango de red previamente asignado, puertos especificados dentro de un arreglo.
```python
#Erick Daniel Blanco de la Garza
#Matricula: 1756734
#Parte 1
#Importamos librerias necesarias
import socket
#Parte 2
#Se define la funcion scan con la cual
#se utilizan sockets para probar diferentes puertos
def scan(addr, port):
	#Creando un nuevo socket
	socket_obj = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

	#Estableciendo el timeout para el nuevo objeto tipo socket
	socket.setdefaulttimeout(1)

	#Conexión exitosa devuelve 0 . Devuelve error en caso contrario
	result = socket_obj.connect_ex((addr, port)) #Direccion y puerto en tupla.

	#Se cierra el objeto
	socket_obj.close()

	return result

#Parte 3
#Lista de puertos a escanear
ports=[21, 22, 25, 80]
#Parte 4
# Bucle por todas las ip del rango 192.168.0.*
for i in range (1,255):
	addr="192.168.0.{}".format(i)
	for port in ports:
		result=scan (addr, port)
		if result ==0:
			print(addr, port, "OK")
		else:
			print(addr, port, "Failed")

```
![scaner2](/FILES/cont/sp2.png "port_scanv2.py")
#
---
### 3. scan_portv4
#### Con este script vizualizamos mucha más información como los protocolos que utiliza nuestro equipo, el estado de la maquina, si está habilitado el TCP, etc.

![scaner4](/FILES/cont/sp4.png "port_scanv4.py")
#
---
### 4. nmap_scan
#### Scrript que junta algunos de los scripts anteriores para automatizar un poco el trabajo.
```python
#Erick Daniel Blanco de la Garza
#Matricula: 1756734
import nmap
escaner = nmap.PortScanner()
print('Escaner de Puertos')
print('Elije un opción')
print('\n\t\t 1-[Escaneo UDP]')
print('\n\t\t 2-[Escaneo completo]')
print('\n\t\t 3-[Detección de sistema operativo]')
print('\n\t\t 4-[Escaneo de red con ping]')
op=int(input('Elije: '))
ip = input('Ingresa la ip a escanear: ')
while True:
	if op == 1:
		escaner.scan(ip, '1-1024', '-v -sV')
		break
	elif op == 2:
		escaner[ip].all_protocols()
		break
	elif op == 3:
		escaner[ip]['tcp'][80]['product']
		break
	else:
		exit()
#No entendí muy bien lo del escaneo de red con ping
```

[Subir](#top)