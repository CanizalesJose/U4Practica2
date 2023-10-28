## U4: Práctica 2

Enlace a repositorio en Github: https://github.com/CanizalesJose/U4Practica2

Esta practica esta centrada en la creación de entornos virtuales de Python para la creación de aplicaciones que se comuniquen con una página HTML usando el módulo Flask.

### Conceptos Básicos
Se crea un archivo python, el cual servirá como nuestro programa y método de comunicación con el servidor.

    from Flask import Flask
    app = Flask(__name__)
    @app.route('/')
    def welcome():
        return 'Bienvenido'

`app = Flask(__name__)` crea un objeto que hace referencia a la instancia de Flask que se ejecuta desde la consola de comandos. `__name__` hace referencia al propio nombre del archivo Script de Python.
Esto permite a la instancia Flask ejecutar la aplicación.

`@app.route('/')` es un método del objeto app que establece una dirección URL que la aplicación puede buscar.

### Rutas
Se pueden generar mas rutas agregando mas métodos `@app.route('/')` o se puede forzar al usuario a acceder a través de una dirección especifica.
Como este es un entorno virtual local, la dirección es `localhost:5000/` o `127.0.0.1:5000/wellcome`.

    from Flask import Flask
    app = Flask(__name__)
    @app.route('/wellcome')
    def welcome():
        return 'Bienvenido'
Con esta modificación, forzamos a entrar desde la dirección `localhost:5000/wellcome`.

### Parámetros
Modificando la ruta y agregando `<name>` se puede agregar un parámetro que se envía al servidor. El parámetro es lo que sea que se escriba en la ruta dentro del navegador.
Modificando la función `welcome()` para que muestra el parámetro agregado.

    from Flask import Flask
    app = Flask(__name__)
    @app.route('/wellcome/<name>')
    def welcome(name):
        return f'Bienvenido {name}'

Es posible especificar el tipo de dato al escribir el parámetro de la siguiente forma: `<type:id>`.
Por tanto, es correcto y posible establecer parámetros específicos como lo son:

    @app.route('/wellcome/<name>')
    @app.route('/wellcome/<int:ncontrol>')

Esto sirve para mandar parámetros, y nos introduce a la capacidad de mandar mas de uno. Esto se hace añadiendo divisores y variables a la ruta de la instancia de Flask.

Por ejemplo, el siguiente código permite acceder a la instancia a través de distintas rutas, en un método que asemeja el polimorfismo. Un caso permite enviar un solo parámetro, otro un parámetro de tipo `string` y un `int` y en otro solo un `int`.

    from flask import Flask

    app = Flask(__name__)

    @app.route('/wellcome/')
    @app.route('/wellcome/<name>')
    @app.route('/wellcome/<int:ncontrol>')
    @app.route('/wellcome/<name>/<int:ncontrol>')

    def bienvenido(name=None,ncontrol=None):

        if name== None and ncontrol==None:

            return 'Bienvenido '

        if name!= None and ncontrol == None:

            return f'Bienvenido {name}'

        if name == None and ncontrol != None:

            return f'El número recibido es: {ncontrol}'

        else:

            return f'Bienvenido {name} tu numero de control es: {ncontrol}'