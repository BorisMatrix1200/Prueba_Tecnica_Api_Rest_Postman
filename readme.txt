=======================================================================
Instrucciones para ejecutar las pruebas de Signup y Login en Demoblaze
=======================================================================

Requisitos previos:
==================

- Tener instalado Postman (https://www.postman.com/downloads/)
  - Si ya tiene una cuenta creada iniciar sesión con usuario y contraseña
    de lo contrario crear un usuario 
- Conexión a internet

================================
Pasos para ejecutar las pruebas:
================================

1. Abrir Postman.

2. Crear una nueva colección llamada "Softka_API_Rest". o Importar el archivo (Softka_API_Rest.postman_collection.json)
   - El archivo (Softka_API_Rest.postman_collection.json) contiene un flujo automatizado de pruebas que se ejecutan
     cada vez que el servicio es consumido o ejecutado.

3. Crear una nueva petición POST para Signup:
   - URL: https://api.demoblaze.com/signup
   - Body (raw JSON):
     {
       "username": "{{randomUser}}",//Se ingresa la variable global creada
       "password": "Password2025+"
     }
   - En la pestaña Scripts - Pre-request se ingresa el siguiente código:

     // Generar un username aleatorio, por ejemplo "user" + 4 dígitos aleatorios
     const randomUser = "user" + Math.floor(Math.random() * 10000);

     // Guardar en variable global
     pm.globals.set("randomUser", randomUser);

     // Mostrar en consola para debug
     console.log("Usuario generado:", randomUser);

   - Enviar la petición para crear un nuevo usuario.

4. Crear otra petición POST para Signup con el mismo usuario para probar usuario duplicado:

   - Repetir el paso anterior con el mismo username y password.
   - Enviar y observar la respuesta para validar manejo de usuario ya existente.

     {
       "username": "Boris Andres",
       "password": "Password2025+"
     }

5. Crear una petición POST para Login con usuario y contraseña correctos:
   - URL: https://api.demoblaze.com/login
   - Body (raw JSON):
     {
       "username": "Boris Andres",
       "password": "UGFzc3dvcmQyMDI1Kw=="
     }
   - Enviar la petición y observar la respuesta.

6. Crear una petición POST para Login con usuario o contraseña incorrectos:

   - Cambiar el username o password a datos incorrectos.
   - URL: https://api.demoblaze.com/login
   - Body (raw JSON):
     {
       "username": "Boris Andres",
       "password": "PasswordIncorrecto"
     }

   - Enviar la petición y observar la respuesta.


================================================
8. Guardar la colección para futuras ejecuciones.
================================================

