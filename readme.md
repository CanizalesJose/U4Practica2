## U4: Práctica 2
Esta practica esta centrada en la creación de entornos virtuales de Python para la creación de aplicaciones que se comuniquen con una página HTML usando el módulo Flask.

### Primer paso
Se crea un archivo python, el cual servirá como nuestro programa y método de comunicación con el servidor.

    from Flask import Flask
    app = Flask(__name__)
    @app.route('/')
    def welcome():
        return 'Bienvenido'

`app = Flask(__name__)` crea un objeto que hace referencia a la instancia de Flask que se ejecuta desde la consola de comandos. `__name__` hace referencia al propio nombre del archivo Script de Python.
Esto permite a la instancia Flask ejecutar la aplicación.

`@app.route('/')` es un método del objeto app que establece una dirección URL que la aplicación puede buscar.

### Segundo paso
