# LLM_Escobar
Repositorio de prueba para implementar LLM y una aplicación web

# 1. Instalación

Cómo primer paso descargamos [ollama] (https://ollama.com/download/linux) de su página web y ejecutamos el siguiente comando:

````bash
$ curl -fsSL https://ollama.com/install.sh | sh
````

# 2. Ejecutar el servidor

Ejecutar el servidor de API REST de ollama , escribiendo en la terminal ollama
la cual arrojara el siguiente menu de comandos

````
Available Commands:
  serve       Start ollama
  create      Create a model from a Modelfile
  show        Show information for a model
  run         Run a model
  pull        Pull a model from a registry
  push        Push a model to a registry
  list        List models
  ps          List running models
  cp          Copy a model
  rm          Remove a model
  help        Help about any command

Flags:
  -h, --help      help for ollama
  -v, --version   Show version information
````
Se usara en la terminal el comando 
````
$ Ollama serve 

````
# 3. Descargar Modelo

En la pagina de ollama descargar un [Modelo] (https://ollama.com/library) utilizando el siguiente comando:

````
$ ollama pull tinyllama

````
Se confirmara que este instalado el modelo con el comando:

````
$ ollama list

````

# 4. Revisar un request a la API REST

Para realizar una consulta utilizamos el comando curl como se muestra en el siguente ejemplo:

````Bash
curl -X POST http://localhost:11434/api/generate -d '{
  "model": "tinyllama",
  "prompt": "Why is the sky blue?"
}'
````

# 5. Realizar un request sin stream

Para realizar una consulta a la API REST sin stream se hace de la siguiente forma:

````Bash
curl -X POST http://localhost:11434/api/generate -d '{
  "model": "tinyllama",
  "prompt": "Why is the sky blue?",
  "stream": false
}'
````

# 6. Consultar a groq

Estructura basica para realizar una consulta a groq mediante API REST

````Bash
curl "https://api.groq.com/openai/v1/chat/completions" \
  -X POST \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer ${GROQ_API_KEY}" \
  -d '{
         "messages": [
           {
             "role": "user",
             "content": "por que el cielo es azul?"
           }
         ],
         "model": "llama3-8b-8192",
         "stream": false
       }'

````

Se debe exportar antes 
````Bash

export GROQ_API_KEY=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

````

#  7. Importar libreria de python

Se importa la libreria Requests se toma de la pagina (https://www.w3schools.com/python/ref_requests_post.asp).

````Bash
import requests

url = 'https://www.w3schools.com/python/demopage.php'
myobj = {'somekey': 'somevalue'}

x = requests.post(url, json = myobj)

print(x.text)

````
- Se adapta a lo que funcionaba pasandolo a python.

````Bash

import requests

url = 'http://localhost:11434/api/generate'
myobj = {
    "model": "tinyllama",
    "prompt": "Why is the sky blue?",
    "stream": False
}

x = requests.post(url, json = myobj)

print(x.text)

````
- Luego se agrega la libreria jason para mostrar en pantalla unicamente el response.

````Bash
import requests
import json

url = 'http://localhost:11434/api/generate'
myobj = {
    "model": "tinyllama",
    "prompt": "Why is the sky blue?",
    "stream": False
}

x = requests.post(url, json = myobj)
x = json.loads(x.text)

print(x["response"])

````