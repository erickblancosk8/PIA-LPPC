
# Nmap
#
__*Los siguientes scripts están hechos en Bash y están enfocados al escaneo de la red mediante el software Nmap que nos proporciona potentes herramientas en sus comandos para analizar información de la red. Previamente se ha instalado una maquina virtual Kioptrix level 1 y se ha configurado en la misma red.*__

### 1. Comando nmap para detectar puertos y servicios disponibles en la mquina kioptrix
#
![puer](/FILES/cont/puer.png "puertos$servicios")
### 2. Comando nmap para detectar si la mquina kioptrix es vulnerable a ataques CCS

![ccs](/FILES/cont/ccs.png "vulenrableaCCS")

### 5. Script Automap
#### Nos permitirá agrupar los scripts anteriormente vistos y automatizar un poco la manera de ejecutarlos desde la consola de comandos.
```bash
#!/bin/bash
#Erick Daniel Blanco De La Garza
#Matricula: 1756734
#
date
	echo "-------------------------"
	echo "	Menu Principal  "
	echo "1. Escaneo de red "
 	echo "2. EScaneo individual "
	echo "3. Escaneo UDP "
	echo "4. Escaneo de script "
	echo "5. Salir"
read -p "Opcion [1 - 6]" c
case $c in
	1) read -p "Ingresa la subred: " inet
	   nmap -sn ${inet} -oN subred_results.txt;;
	2) read -p "Ingresa la ip a escanear: " ip
	   sudo nmap -v -A ${ip} -oN ip_results.txt;;
	3) read -p "Ingresa la ip a escanear: " ip_1
	   nmap -sU ${ip_1} -oN UDP_results.txt;;
	4) read -p "Ingresa la ip a para escanear los scripts: " ip_2
	   nmap -sC ${ip_2} -oN script_results.txt;;
	5) echo "Bye!"; exit 0;;
esac

```

[Subir](#top)