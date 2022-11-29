# Encoding&Decoding

#
__*Los siguientes scripts están hechos en Python y son herramientas que nos permitiran manipular la información para realizar la codificación y decodificación de archivos en base64. Analizaremos ciertas sentencias y estructuras al igual que las librerias que nos permiten realiazar estos cifrados en Python.*__
### 1. encode_text
##### Script en Python que desencripta un mensaje de base64 mediante una llave de cifrado 
```python
#Erick Daniel Blanco De La Garza
#Matricula : 1756734
#Importamos fernet desde cryptography
#
from cryptography.fernet import Fernet
#Definicion de la funcion genwrite que genera una llave
#para cifrarlo
def genwrite():
	key = Fernet.generate_key()
	with open("pass.key","wb") as key_file:
		key_file.write(key)
#Llamamos a la funcion para generar el archivo "pass.key"
#que contiene la llave
genwrite()

#Definicion de la funcion call_key con la cual leemos
#el contenido del archivo "pass.key"

def call_key():
	return open("pass.key", "rb").read()

#
#Ahora ciframos un mensaje almacenado y codificado previamente

key = call_key()
banner = "Hoy es un buen dia para programar".encode()
a = Fernet(key)
coded_banner = a.encrypt(banner)
print(coded_banner)
#
#Ahora desciframos el mensaje previamente cifrado
key = call_key()
b = Fernet(key)
print("\n")
decoded_banner = b.decrypt(coded_banner)
print(decoded_banner)
#
#Fin del script

```
![cyper.py](/FILES/cont/cyper.png "cyper.py")

---

### 1. encode_imgur
##### Script en Python para codificar y decodificar una imagen desde una url
```python
#Erick Daniel Blanco De La Garza
#Matricula : 1756734
import requests # Para hacer un request a un sitio
import base64 # Para Encode/Decode en base64
from requests import Response
#
## Para descargar la imagen del sitio
#
if __name__ == '__main__':
	url = "https://<URL>"

	Response: Response = requests.get(url, stream=True)
	with open('houses.jpg', 'wb') as file_down:
		for chunk in Response.iter_content() : #Descargando contenido poco a poco
			file_down.write(chunk)
	Response.close()

#
## Para codificar la imagen
#
with open('houses.jpg', 'rb') as binary_file:
	binary_file_data = binary_file.read()
	base64_encoded_data = base64.b64encode (binary_file_data)
	base64_message = base64_encoded_data.decode ('utf8')

	print(base64_message)
```

[Subir](#top)