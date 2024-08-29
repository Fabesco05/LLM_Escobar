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



