# Webscraping
#
__*Los siguientes scripts están hechos en Python y son herramientas que nos permitiran recolectar información y manipularla por medio de librerias que nos permitiran realizar el webscraping.*__
### 1. scrap1
##### Script en Python que obtiene el html completo de una URL de github
```python 
# Importar modulos
#Erick Daniel Blanco De La Garza
#Matricula: 1756734
import time
import requests
print ("Hora: ",time.strftime("%I:%M:%S"))
print ("Fecha: ",time.strftime("%d/%m/%y"))
# Obteniendo la informacion HTML de la URL
URL = "https://realpython.github.io/fake-jobs/"
page = requests.get(URL)
# Imprimir el texto de la peticion GET
print(page.text)

```
![web1.py](/FILES/cont/web1.png "web1.py")

---

### 2. scrap5
##### En este script filtramos mas la información que necesitamos detallar en la misma URL de github
```python
# Importar modulos
# Erick Daniel Blanco De La Garza
# Matricula: 1756734
import requests
from bs4 import BeautifulSoup
import time
print ("Hora: ",time.strftime("%I:%M:%S"))
print ("Fecha: ",time.strftime("%d/%m/%y"))
# Obteniención los datos de la peticion GET
URL = "https://realpython.github.io/fake-jobs/"
page = requests.get(URL)
# Analizamos el contenido HTML con BeautifulSoup
soup = BeautifulSoup(page.content, "html.parser")
results = soup.find(id="ResultsContainer")
# Buscar todos los elementos del class "card-content"
job_elements = results.find_all("div", class_="card-content")
# En el objeto job_elemento buscamos solo aquellos elementos
# con titulo e información relevante.
for job_element in job_elements:
	title_element = job_element.find("h2", class_="title")
	company_element = job_element.find("h3", class_="company")
	location_element = job_element.find("p", class_="location")
	# Se imprime solo el texto sin los espacios en blanco
	print(title_element.text)
	print(company_element.text)
	print(location_element.text)
	print()
    
```
![web12.py](/FILES/cont/web2.png "web2.py")
### 3. scrap7
##### En este script filtramos solo la fecha y la cantidad de elementos que estamos obteniendo en la URL
```python
![web2.py](web2.png "web2.py")
# Importar modulos
# Erick Daniel Blanco De La Garza
# Matricula: 1756734
import requests
from bs4 import BeautifulSoup
import time
print ("Hora: ",time.strftime("%I:%M:%S"))
print ("Fecha: ",time.strftime("%d/%m/%y"))
# Obteniención los datos de la peticion GET
URL = "https://realpython.github.io/fake-jobs/"
page = requests.get(URL)
# Analizamos el contenido HTML con BeautifulSoup
soup = BeautifulSoup(page.content, "html.parser")
results = soup.find(id="ResultsContainer")
# Buscar todos los elementos del class "card-content"
job_elements = results.find_all("div", class_="card-content")
# Buscar todos los elementos que el h2 contenga en su texto
# la palabra "python"
python_jobs = results.find_all (
	"h2", string=lambda text: "python" in text.lower()
	)
#Mostramos la cantidad de elementos que cumplen la busqueda
print(len(python_jobs))
```
![web3.py](/FILES/cont/web3.png "web3.py")
### 4. scrap12
##### En este script filtramos de nuevo y obtenemos ahora las URLs donde apuntan los elementos que vizualizamos anteriormente
``` python
# Importar modulos
# Erick Daniel Blanco De La Garza
# Matricula: 1756734
import requests
from bs4 import BeautifulSoup
import time
print ("Hora: ",time.strftime("%I:%M:%S"))
print ("Fecha: ",time.strftime("%d/%m/%y"))
# Obteniención los datos de la peticion GET
URL = "https://realpython.github.io/fake-jobs/"
page = requests.get(URL)
# Analizamos el contenido HTML con BeautifulSoup
soup = BeautifulSoup(page.content, "html.parser")
results = soup.find(id="ResultsContainer")
# Buscar todos los elementos del class "card-content"
job_elements = results.find_all("div", class_="card-content")
# Buscar todos los elementos que el h2 contenga en su texto
# la palabra "python"
python_jobs = results.find_all(
	"h2", string=lambda text: "python" in text.lower()
	)
# Buscamos cada elemento que tenga de referencia de python_jobs
# y almacenarlo en python_jobs_elements
python_jobs_elements = [
	h2_element.parent.parent.parent for h2_element in python_jobs
	]
# Mostrar información de python_jobs_elements
for job_element in python_jobs_elements:
	title_element = job_element.find("h2", class_="title")
	company_element = job_element.find("h3", class_="company")
	location_element = job_element.find("p", class_="location")
	# De la lista de elementos de la etiqueta "a" buscamos
	# el primer elemento que incluya href.
	link_url = job_element.find_all("a") [1]["href"]
	print(company_element.text.strip())
	print(location_element.text.strip())
	print(title_element.text.strip())
	# Imprimimos la salida con link_url
	print(f"Apply Here: {link_url}\n")
	print()
```
![web4.py](/FILES/cont/web4.png "web4.py")

[Subir](#top)