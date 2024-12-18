# REST

!!! note "Representational State Transfer(REST)"
> Utiliza estándares existentes como HTTP.
> Comunicación Client-Server.

## Características del REST
- Arquitectura Client-Server.
- Stateless.
- Cacheable.
- Expone recursos(URIs)
- Usa explícitamente los verbos HTTP.
- Navegable.
- [[14-REST-Security]]


!!! warning "Stateless"

- Cada request se ejecuta de forma independiente al resto.
- Cada request contiene toda la información necesaria para completarse.
- La API no mantiene ningún tipo de sesión.
- Se promueve el uso de tokens para el manejo de la seguridad.


!!! warning "Cacheable"
- Es la capacidad de estos sistemas para etiquetar de alguna forma las respuestas para que otros mecanismos intermedios funcionen como un cache.
- Estos sistemas o mecanismos intermedios deben ser por lo general transparentes para los desarrolladores, no deben afectar la manera en que los servidores se consumen.
- Reduce el ancho de banda usado.
- Reduce la latencia.
- Reduce la carga en servidores.
- Oculta fallos de red.

![[Pasted image 20240927083631.png]]

!!! warning "Compresion"
> Las APIs suelen retornar representaciones en varios formatos, entre ellos el formato plano, XML, JSON, etc, y estos formatos pueden ser comprimidos para ahorrar ancho de banda sobre la red.

![[Pasted image 20240927083809.png]]



!!! warning "Uniform Resource Identifier(URI)"

- Identificacion univoca de recursos con cadenas de caracteres.
- Identifica los recursos por clase o tipo.
- Uso de sustantivos en plural por convención. **NO verbos**.
- Distinción de recursos principales y subordinados.

![[Pasted image 20240927084054.png]]


# HTTP Requests

!!! warning "Verbos HTTP - Requests"

- **GET**: Solicita una representacion de un recurso especifico.
- **POST**: Se utiliza para enviar una entidad a un recurso en especifico.
- **DELETE**: Borra un recurso en especifico.
- **PUT**: Reemplaza todas las representaciones actuales del recurso de destino con la carga util de la petición.
- **PATCH**: Aplica modificaciones parciales a un recurso(A diferencia de PUT).
- **OPTIONS**: Es utilizado para describir las opciones de comunicación para el recurso de destino.


!!! warning "HTTP Status Codes - Responses"

- 1XX: Informational.
- 2XX: Success.
- 3XX: Redirection.
- 4XX: Client Error.
- 5XX: Server Error.

![[Pasted image 20240927084517.png]]


!!! note "Versionado"
> REST no provee un mecanismo definido para versionado, pero se suelen ver estas estrategias:

![[Pasted image 20240927160552.png]]



!!! warning "Respuestas"
> - Mantener los mas estandarizadas a las mismas.
> - Reducir el tamaño de la respuesta a lo necesario.
> - Utilizar Códigos de Errores HTTP.

![[Pasted image 20240927160737.png]]


> [!info] Paginados, Filtros y Ordenamientos
> Suelen usarse como parámetros del queryString o del body.

![[Pasted image 20240927161007.png]]


!!! note "Logging, Health, Metrics"
> Tener logs, métricas y puntos de control ayudan a detectar los problemas antes de que realmente lleguen. 
> Se suelen agregar endpoints para verificar o monitorear que la API está viva, y obtener datos de uso de memoria, etc.
