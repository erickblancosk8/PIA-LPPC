# Envio de correos
#
__*Los siguientes scripts están hechos en Python y están enfocados al envio de correos mediante el librerias y sentencias que nos permitiran automatizar el envio de correos hacia un destino con la simple ejecución del script.*__
#
### 
## 1. mailsender
#### Script en Python para enviar un correo desde la terminal con solo ejecutar el script que tiene dentro ya la información para el remitente y destinatario como el adjunto a enviar, el asunto y el mensaje del mismo. Todo esto en un agradable formato de HTML
#

```python
#Erick Daniel Blanco De La Garza
#Matricula:1756734
#Importando librerias necesarias para el envío y los adjuntos en los mails
from email.message import EmailMessage
import smtplib
remitente = ""
destinatario = "gerardo.bernal@uanl.edu.mx "
mensaje = """<head><strong>Practica 12</strong><head/></br>
</br><body>Ejercicio de la Practica 12 para envío de correos. 
</br></br><strong>Alumno: </strong>Erick Daniel Blanco De La Garza
</br></br><strong>Matricula: </strong>1756734</body>"""
#Metodo para llenar la información del remitente, destinatario y asunto del mail
email = EmailMessage()
email["From"] = remitente
email["To"] = destinatario
email["Subject"] = "Prueba de envío (script python) 1756734"
email.set_content(mensaje, subtype="html")
#Metodo open para abrir el archivo que queremos adjuntar
with open("C:/Users/sdela/OneDrive/Escritorio/saa/fcfm_cool.png", "rb") as f:
    email.add_attachment(
        f.read(),
        filename="fcfm_cool.png",
        maintype="fcfm_cool.png",
        subtype="png"
    )
   #Parametros SMTP para indicar el servidor y el puerto para realizar el envío
smtp = smtplib.SMTP("smtp.gmail.com", port=587)
#smtp = SMTP("smtp.gmail.com", port=587)
smtp.starttls()
smtp.login(remitente, "")
smtp.sendmail(remitente, destinatario, email.as_string())
smtp.quit()

```
## 2. Correos con Python IDLE
### Sentencia de comandos en Python IDLE para enviar correos electeronico.
![correo](/FILES/cont/co1.png "correosIDLE")
#

[Subir](#top)