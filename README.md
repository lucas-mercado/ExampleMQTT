# ExampleMQTT

En este repositorio implementare un ejemplo simple usando el protocolo mqtt y el lenguaje de progracion python.
En principio se mostrara como correr broker mosquitto y generar dos clientes, uno sub y otro pub, para observar como interactuan. 

### Pre-requisitos 📋

_Instalacion del Broker Mosquitto y mosquitto_clients_
  
  * https://mosquitto.org/

# Ubuntu
Mosquitto esta disponible en el repositorio de ubuntu entonces puede instalar como cualquier otro paquete. Si tiene una versión anterior de Ubuntu o desea una versión más reciente de mosquitto, agrege el mosquitto-dev PPA para su lista de repositorio -ver el link https://launchpad.net/~mosquitto-dev/+archive/ubuntu/mosquitto-ppa para mas detalles. Mosquitto entonces puede ser instalado desde su package manager.

_agregamos el package de mosquitto a SO Ubuntu_

```
  # sudo apt-add-repository ppa:mosquitto-dev/mosquitto-ppa
  # sudo apt-get update
```
_Install broker and client_:
```
  # sudo apt-get install mosquitto
  # sudo apt-get install mosquitto-clients
```
### Run Broker Mosquitto

generar archivo de conf para mosquitto(mosquitto.conf).
configuracion simple:
  * generate file: mosquitto.conf
    ```  
    # port y ip en donde va estar escuchando el broker.
    listener 1883 127.0.0.1
    #permite user anonimos.
    allow_anonymous true
    ```
para mas detalles sobre el armado del archivo de configuracion leer la doc de eclipse Mosquitto @see https://mosquitto.org/man/mosquitto-conf-5.html. 

### Ejemplo:

_ejemplo de sub y pub desde la terminal (debe tener corriendo broker mosquitto)_.

* subcripcion al broker,al topic "mje" y imprimira (topic y mensaje). 
``` 
  mosquitto_sub -h 127.0.0.1 -p 1883 -t "mje" -v
  result => mje {mje:'Hola Mundo'}
``` 
* publicar al broker y al topic "mje"
``` 
  mosquitto_pub -h 127.0.0.1 -p 1883 -t "mje" -m "{ mje: 'Hola Mundo' }"
``` 
