# REST Security Design Principles
- Least Privilege: Tener el menor privilegio requerido para hacer las acciones.
- Fail-Safe Defaults: Por defecto no tener acceso a los recursos.
- Complete Mediation: El sistema debe validar los permisos de acceso a todos los recursos.
- KISS.
- Uso de HTTPS.
- Password Hashes.
- Never expose information on URLs.
- Considerar agregar Timestamp en los requests.
- Validación de los parámetros de entrada.


> [!WARNING] Monitorizacion de transacciones sospechosas

- Cantidad de requests por IP o por token/JWT/user para evitar problemas de DoS, o simplemente controlar o reducir el uso excesivo que puede bajar la performance de la API en general.
- Limitación de velocidad, o tiempos de demora agregados entre requests para ciertos casos, ayuda a reducir las solicitudes excesivas que ralentizarían la API, ayuda a lidiar con llamadas/ejecuciones accidentales y monitorea e identifica de manera proactiva una posible actividad maliciosa.


## Authentication y Authorization


> [!IMPORTANT] Basic Auth
> Base64 encoding: Es fácilmente codificable, y se debería usar en conjunto con otro mecanismo de seguridad como HTTPS/SSL.

![](Ingeniería%20de%20Software%20I/img%20is1/Pasted%20image%2020240927155022.png)


> [!IMPORTANT] API Keys
> Algunas APIs usan API keys para autorizacion.
> Una API key es un token que el cliente provee cuando hace la llamada via queryString.
> Se supone que las API keys son secretas y que solo el cliente y el servidor la conocen. 
> Solo debería usarse en conjunto con otro mecanismo de seguridad como HTTPS/SSL.

![](Ingeniería%20de%20Software%20I/img%20is1/Pasted%20image%2020240927155218.png)



> [!IMPORTANT] Bearer Authentication/ Token Auth
> Utiliza tokens de seguridad llamados Bearer, que da acceso al portador del token.

![](Ingeniería%20de%20Software%20I/img%20is1/Pasted%20image%2020240927155330.png)



> [!IMPORTANT] OAuth
> Es un protocolo de autenticacion.
> Consiste en delegar la autenticacion de usuario al servicio que gestiona las cuentas, de modo que sea este quien otorgue el acceso para las aplicaciones de terceros.
> OAuth2 provee un flujo de autorización para aplicaciones web, aplicaciones móviles e incluso programas de escritorio.

![](Ingeniería%20de%20Software%20I/img%20is1/Pasted%20image%2020240927155547.png)


> [!IMPORTANT] Autenticación y Autorización JWT
> El token se genera en el primer paso tambien.
> Las credenciales del usuario viajan solo 1 vez.
> El token no se almacena del lado del servidor para validar.
> El uso de JWT incrementa la eficiencia en las aplicaciones evitando hacer multiples llamadas a la base de datos.


![](Ingeniería%20de%20Software%20I/img%20is1/Pasted%20image%2020240927155816.png)

![](Ingeniería%20de%20Software%20I/img%20is1/Pasted%20image%2020240927155929.png)

- Los JWT pueden ser mensajes solo firmados, solo encriptados, o ambos.
- Si un token es solo firmado pero no encriptado, cualquiera puede leer su contenido, pero si no se conoce la clave privada no puede ser modificado, ya que al validar la firma no coincidiría.
![](Ingeniería%20de%20Software%20I/img%20is1/Pasted%20image%2020240927160053.png)

- El server valida la firma del JWT para saber que lo que él le envió al cliente no se modificó, y utiliza la información del mismo.
- De esta forma se sigue siendo stateless, y generalmente se hace más eficiente la validación del usuario, sin tener que acceder a un medio persistente a validar si el token es válido y a quién pertenece el mismo.

![](Ingeniería%20de%20Software%20I/img%20is1/Pasted%20image%2020240927160235.png)


> [!IMPORTANT] Refresh Tokens
> Los access token deberían tener un tiempo limitado de vida, por eso aparecen los refresh token.
> Este es otro token que sirve para un solo uso y es utilizado para obtener un nuevo access token.
> Es una credencial que permite obtener nuevos tokens sin necesidad de usar las credenciales de usuario y password nuevamente.
