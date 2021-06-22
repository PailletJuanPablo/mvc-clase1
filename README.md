
# MVC

- Visualizar la vista con el formulario de login (input email, password, boton enviar)

- Se realiza petición al servidor. 
- Router de express,
    - Recibo una petición POST a /login
        app.post('/login')
        app.get('/login', )
    Router vincula rutas a controladores
    Le pasa al controlador req, res
         app.post('/login', controladorUsuario.login)

- 1)Rutas -> Dispatcher: Dispara o da comienzo a la lógica de 2)MVC

- Ruta va a apuntar a un controlador, a un método de un controlador

    - Verifico que en el body de la petición tenga un email y password
        - La petición no tiene email y password: Devolver una respuesta con una vista de error: Debe completar email y password.

        - Controlador -> Modelo Usuario 
            -> Existe un usuario con este email ?
                -> No existe -> Devuelve una respuesta con vista de error
                -> Si existe
            
        - Controlador -> Modelo Usuario
            -> ¿La clave del usuario que existe coincide con la que me envió el cliente?
                -> No coinciden -> Devuelve respuesta con vista de error
                -> Si coincidan
        
        - Controlador -> Modelo Publicacion
            -> Dame todas las publicaciones que puede ver este usuario

        - CONTROLADOR
            - datos del controlador: {
                usuario: {
                    nombre: 'Jorge',
                    email: 'jorge@gotmail.com'
                },
                posts: [
                    {
                        imagen: 'sadas.png',
                        texto: 'Hola',
                        usuario: {AMIGO DEL USUARIO QUE HIZO LA PETICIÓN}
                    }
                ]
            }
        
        - Controlador -> Modelo Mensaje
                            -> Dame todos los mensajes del usuario

        - DATOS DEL CONTROLADOR
            {
                usuario: {....},
                posts: [...],
                mensajes: [...],
                token: 'asdjdki122382191o12lads**'
            }

        - Controlador   -> Le pasa sus datos a la VISTA.
                        -> Devolver una respuesta con la vista

        - VISTA == Presentación
            - Recibo un objeto usuario
            - Recibo un array de posts
            - Recibo un array de mensajes

## Ejemplo de persistir sesión

- En la próxima petición -> Controlador verifica el token del cliente -> Lo desencripta -> Decide si puede continuar logueado
            -> Devuelve la vista a la que quería acceder
            -> Vista que informa que "Su sesión expiró" formulario de login

        
## Vista detalle producto

    <div class="fotoProducto">
        MOSTRAR LA IMAGEN QUE ME PASE EL CONTROLADOR
    </div>
    <h2 class="tituloproducto"> TITULO QUE ME PASA EL CONTROLADOR </h2>


# Actividad MVC

- npm init -y
- npm install express
- .gitignore -> node_modules