# Repaso Final


## Repaso Parcial 2C24
1. Refactorizar el siguiente fragmento de código:

```
…SomeClass…{
	…
	bool wasInitialized(){
		return…
	}
	
	someFunction… {
		if ((platform.toUpperCase().indexOf("MAC") > -1) 
			&& (platform.toUpperCase().indexOf("IE") > -1)
			&& wasInitialized() 
			&& resize > 0) {
		  someCode();
		} 
		otherCode();
		}
}
```
Este codigo viola el principio de Open Closed, debido a que si queremos agregar una nueva `platform`, tendremos que modificar el comportamiento interno de la clase. Ademas, si suponemos que el metodo `wasInitialized` nos devuelve un estado interno de la clase, estariamos tambien violando este principio, porque en un futuro podriamos querer agregar algun estado nuevo, y tendriamos que tocar de nuevo el codigo interno de la clase.

Se propone:
- Crear una abstracción para manejar la plataforma: de esta forma cada plataforma define su comportamiento interno, y `someFunction` simplemente debería llamar al método de la clase(obviamente, `SomeClass` ahora tendría que conocer su plataforma).
- Utilizar el patrón de diseño `State` para manejar el estado la clase(lo que corresponde con el método `wasInitialized`).

Con estos cambios no se viola el principio de Open Closed, y si en un futuro se quisiera extender a `SomeClass`, se podría hacerse sin tener que modificar su código interno.

2. Nombre las ceremonias de Scrum y detalle brevemente cada una.

![](Ingeniería%20de%20Software%20I/img%20is1/Pasted%20image%2020240925154736.png)


3. Explique las ventajas del uso del modelo de vistas de 4+1 para una arquitectura de software, haga un ejemplo de una posible vista de despliegue.

	Modelar nuestras arquitecturas con el Modelo de Vistas 4+1 nos da las siguientes ventajas:
	- Permite a través de diferentes vistas analizar distintas perspectivas del problema, focalizándose en el problema en cuestión.
	- Concentra en un único documento las principales decisiones tomadas sobre el sistema.
	- Permite a nuevos integrantes del equipo entender la arquitectura del sistema y ubicarse dentro de la solución.
	- Permite discutir con todos los stakeholders las distintas decisiones y validarlas en una etapa temprana.


4. ¿Qué es refactoring? Como se asegura de lograrlo. De un ejemplo simple con código.

	El Refactoring consiste en modificar el código interno de alguna clase, método o función, sin modificar su comportamiento interno. La idea de aplicar refactoring surge de la necesidad de mejorar la calidad del código, aplicando en lo posible buenas prácticas, y adecuándose a un mejor diseño siguiendo heurísticas y patrones de diseño. 
	
	Mediante el uso de tests unitarios de los fragmentos que vayamos a refactorizar, nos aseguramos de no modificar el comportamiento externo de lo que cambiemos.

5. ¿Qué es un code smell? Nombre dos, y ejemplifíquelos con código.

	Es cualquier característica en el código fuente de un programa que posiblemente indique un problema más profundo. Los code smell aparecen cuando al revisar fragmentos de código, se detectan malas prácticas tanto semánticas(por ejemplo un código con demasiados comentarios), como de diseño(por ejemplo si se viola algún principio SOLID, o si tenemos funciones con demasiados parámetros).

6. Qué diferencia un token tradicional de un token JWT, comente las ventajas y desventajas.

	Al utilizar tokens tradicionales, se pasan las credenciales para todas las operaciones que quiera hacer el usuario(normalmente codificadas con Base64). Esta forma es bastante sencilla, pero es insegura, debido a que vamos a estar constantemente pasando nuestras credenciales.
	Al utilizar tokens JWT, las credenciales viajan una sola vez: Se validan las credenciales, y se pasa el token. El servidor no guarda los tokens, sino que conoce un mecanismo para validar tokens firmados por el(es stateless). Al tener esta verificación, el usuario debe colocar sus credenciales una sola vez, y luego se utiliza el token JWT para validar su identidad en el servidor.

7. ¿Qué significa autenticar y que autorizar. De 3 ejemplos diferentes de cómo podría autenticarse a un usuario en un sistema.

	Autenticar es validar la identidad de un usuario en el sistema. Esto se suele mediante el pedido de credenciales de parte del servidor. Autorizar es tomar esa identidad, y verificar que permisos tiene dentro del sistema(que acciones puede realizar, y cuales no).

8. ¿Cuáles son los síntomas de un mal diseño? Detalle brevemente cada uno.

	- Rigidez: quiero modificar algo y tengo que cambiar cosas en 35 lugares.
	- Fragilidad: toco algo de algún lado y se rompe algo en otro.
	- Inmovilidad: quiero mover ciertas funcionalidades de un lado a otro y no puedo. Está todo demasiado acoplado.

9. ¿Qué es la inversión de dependencia? Explique y dé un ejemplo de código.

	Los módulos de alto nivel no deben depender de módulos de bajo nivel. Ambos deben depender de abstracciones. Las abstracciones no deberían depender de detalles (implementaciones concretas). Los detalles deberían depender de abstracciones.

10. ¿Se viola algún/os principio SOLID? En caso afirmativo indicar cuál/es, y cómo lo resolvería.

	```
	public class MileageCalculator {  
	    private List<Car> cars;  
	    public MileageCalculator(List<Car> cars) {  
	        this.cars = cars;  
	    }  
	    public void CalculateMileage() {  
	        for (Car car : cars) {  
	            if (car.name.equals("Audi")) {  
	                System.out.println("Mileage of the car " + car.name + " is 10M");  
	            } else if (car.name.equals("Mercedes")) {  
	                System.out.println("Mileage of the car" + car.name + "is 20M");  
	            }  
	        }  
	    }  
	}
	```

	- Open Closed: Si quiero agregar mas tipos de autos, voy a tener que tocar el código fuente de `MileageCalculator`(Es rígido). La forma de resolver este problema es creando clases concretas para cada tipo de auto, y aprovechar el polimorfismo para que solamente se haga una llamada en `CalculateMileage`.
	- Single Responsibility: La clase tiene varias razones de cambio: por ahora hace el calculo de millas, pero también es responsable de printear por consola el mensaje de salida. Esto se resuelve reduciendo las razones de cambio de esta clase mediante el uso de delegación de responsabilidades(se podría crear otra clase responsable de la acción que realiza cada auto al llamarse el `calculatemileage`.

11. Explique el mecanismo de Autenticación Basic Authentication, y como lo utiliza en una API Rest.

	Tomo mis credenciales(username, password, etc), las codifico en Base64, y cuando quiera autenticarme en un sistema, simplemente agrego estas credenciales en el campo `Authorization` en las llamadas a la API REST. 

12. Haga un diagrama de secuencia explicando cómo se realiza un login que retorna un token JWT y como luego se accede a un servicio que requiere autenticación.

![](Ingeniería%20de%20Software%20I/img%20is1/Pasted%20image%2020240927160053.png)

![](Ingeniería%20de%20Software%20I/img%20is1/Pasted%20image%2020240927160235.png)


13. A qué nos referimos por Calidad Semántica de las historias de usuario.
![](Ingeniería%20de%20Software%20I/img%20is1/Pasted%20image%2020240925160056.png)

14. ¿Qué son los criterios de aceptación? ¿Qué características se desea que tengan?  Escriba una historia de usuario y defina los criterios de aceptación para la misma

> [!IMPORTANT] Criterios de Aceptación
> Condiciones específicas que deben cumplirse para aceptar trabajo realizado.
> Deben ser claros, concisos, verificables, independientes y orientados al problema.



---
## Parcial Memo II 1C24
### Ejercicio 1
![](Ingeniería%20de%20Software%20I/img%20is1/Pasted%20image%2020241206175757.png)

1. Login de usuarios: 
	- Endpoint: `POST /api/v1/auth/login`
	- Body: `{"username": <username>, "password": <password>}`
	- Respuesta: `{"accessToken": <JWT_access_token>, "refreshToken": <refresh_token>}`
2. Renovación del token:
	- Endpoint: `POST /api/v1/auth/refresh`
	- Body: `{"refresh_token": <refresh_token>}`
	- Respuesta: `{"accessToken": <JWT_access_token>}`
3. Registro de Usuarios:
	- Endpoint: `POST /api/v1/user/register`
	- Body: `{"username": <username>, "password": <password>, "firstName": "Juan", "lastName": "Pérez", "dateOfBirth": "1990-01-01", "gender": "male", "avatarUrl": "https://example.com/avatar.jpg"}`
	- Respuesta: `201 Created`
4. Listar eventos: 
	- Endpoint: `GET /api/v1/events`
	- Query Parameters: `name, date, location`(todos opcionales).
	- Respuesta: `{ "currentPage": 1, "pageSize": 10, "totalPages": 5, "totalItems": 50, "events": [{ "id": 1, "name": "Maratón Bogotá", "date": "2024-01-20", "location": "Bogotá", "details": "Evento anual de running.", "photoUrl": "https://example.com/photo.jpg" }]}
`
### Ejercicio 2
![](Ingeniería%20de%20Software%20I/img%20is1/Pasted%20image%2020241206175101.png)

Un atributo de calidad es una medida o propiedad testeable que tiene un sistema, y sirve para indicar cómo satisface las necesidades de sus stakeholders. 


> [!NOTE] Disponibilidad
> Capacidad del sistema para estar en funcionamiento y accesible cuando se lo necesita.
> Es esencial para garantizar que los sistemas de software cumplan con las expectativas de los usuarios y las necesidades del negocio.
> Se deben implementar estrategias para mitigar fallos y garantizar la continuidad del servicio.


> [!NOTE] Performance
> Tiempos de respuesta de la aplicación en relación a las funcionalidades o actividades soportadas por la misma.
> Se consideran dos métricas para medir el rendimiento de una aplicación:
> 	- **Latencia**: Tiempo dedicado a responder un evento.
> 	- **Capacidad**: El número de eventos que pueden ocurrir en un tiempo determinado.

Si desarrollamos interfaces muy poco usables(difíciles de usar, incomprendibles, ...), los usuarios pueden llegar a ignorar la protección de sus datos y cuentas. Es primordial desarrollar aplicaciones que sean usables para una amplia cantidad de usuarios, y que además les permita adoptar medidas de seguridad de una manera sencilla para proteger sus datos.

### Ejercicio 3
![](Ingeniería%20de%20Software%20I/img%20is1/Pasted%20image%2020241206104043.png)

Code Smells:
1. Uso excesivo de getters(viola Tell, Don't Ask). 
2. Viola encapsulamiento -> El método accede a los datos de otro objeto.
3. Long Method y Message Chains.

Principios SOLID que se violan:
1. Single responsibility: porque si el día de mañana se agrega mas comportamiento cuando se envía un sendSMS o un sendDiscord, el método tendría mas de una razón de cambio, y por lo tanto viola el principio. 
2. Open Close: Booleanos por parámetro -> El día de mañana quiero enviar mensajes por otro medio y debería agregar otro parámetro y otro condicional más, haciendo mas difícil mantener el código. 

### Ejercicio 4
1. Explique las ventajas y desventajas del flujo de trabajo Trunk-Based en Git, en el cual se trabaja en un único branch principal.

	La ventaja principal de este flujo de trabajo es su simpleza, debido a que solo se maneja un único branch, y el equipo de desarrollo no maneja múltiples branches. El código está en el último commit de esta branch, y eso puede ser una desventaja muy grande porque es muy complicado separar líneas de trabajo, y si tenemos un equipo que cada vez es más grande, terminamos teniendo muchos conflictos para manejar el entorno. Esto tiene como causa principal de que Git además de ser distribuido, es concurrente: tenemos que asegurarnos de que varias personas pueden trabajar en un mismo espacio de trabajo a la vez(concurrentemente), y justamente este flujo de trabajo trae muchos problemas para trabajar concurrentemente. Se vuelve inmanejable si tenemos un equipo grande.


2. Escriba los comandos y el comentario del commit asociado a una tarea para realizar el cambio de pasar como dato obligatorio a la fecha de nacimiento ya que solo se podrán registrar personas de más de 16 años.

	`git branch` -> Con esto vemos la branch actual.
	`git checkout [-b] <nombre_de_la_nueva_branch>` -> En caso de querer hacer el commit en otra branch, se hace checkout a la branch deseada.
	`git status` -> Con esto detectamos los archivos que fueron cambiados, para que al hacer `add` solamente agreguemos los que nos interesan para el commit.
	`git add <archivos_que_interesan>` -> Con esto agregamos para el commit los archivos que nos interesan. Si hacemos `git add .`, puede pasar que agreguemos archivos "de más" para nuestro commit(La idea es que los commits sean atómicos y acordes a lo que se va a especificar en el comentario del commit, no tiene sentido agregar otras cosas).
	`git commit -m <mensaje_del_commit>` -> Con esto se realiza el commit a la branch actual.

	Mensaje del commit: "feat: se pasa como dato obligatorio a la clase Registrador la fecha de nacimiento del nuevo usuario, debido a que solo se pueden registrar personas de más de 16 años.".

---

## Parcial IS1 2C24

![](Ingeniería%20de%20Software%20I/img%20is1/Pasted%20image%2020241209101508.png)

1. La vista de Desarrollo(o componentes) nos muestran la organización de módulos de software en el ambiente de desarrollo del sistema. Normalmente es utilizada por los desarrolladores, ya que van a tener una visión más específica sobre los componentes que componen al sistema en conjunto. Tiene en cuenta los requisitos internos relativos a la facilidad de desarrollo, administración del software, reutilización y elementos comunes, y restricciones impuestas por las herramientas o el lenguaje de programación que se use.

	Ejemplo(del TP grupal):

![](Ingeniería%20de%20Software%20I/img%20is1/Pasted%20image%2020241209101851.png)


![](Ingeniería%20de%20Software%20I/img%20is1/Pasted%20image%2020241209101931.png)

2. El Burndown Chart es una representación gráfica del trabajo por hacer en un proyecto en el tiempo. Usualmente el trabajo remanente (o _backlog_) se muestra en el eje vertical y el tiempo en el eje horizontal. Es decir, el diagrama representa una serie temporal del trabajo pendiente. Este diagrama es útil para predecir cuándo se completará todo el trabajo.

![](Ingeniería%20de%20Software%20I/img%20is1/Pasted%20image%2020241209102255.png)


![](Ingeniería%20de%20Software%20I/img%20is1/Pasted%20image%2020241209102342.png)

3. Se están usando demasiados valores para asignarle peso a las tareas. En primer lugar, habría que reducir la cantidad de valores que tiene la secuencia: yo usaría de 5 a 7 valores, no más. Lo que pasa al usar muchos valores es que crecen muy rápido en Fibonacci, y por eso se ve mucha diferencia entre valores. Lo que también ayudaría es "atomizar" las tareas a realizar: esto va a ayudar a reducir las diferencias en las ponderaciones de los integrantes, y las tareas van a reducir su peso, ya que son más pequeñas y más sencillas.

![](Ingeniería%20de%20Software%20I/img%20is1/Pasted%20image%2020241209102813.png)

4. Inciso 1:
	1. Envío de emails -> Como usuario quiero poder enviar emails para comunicarme con otros usuarios.
	2. Guardado de contactos -> Como usuario quiero poder guardar contactos, para facilitar el enviado de emails.
	3. Vista de casilla de mensajes -> Como usuario quiero poder ver mi casilla de mensajes para ver quien se quiso comunicar conmigo.
	Inciso 2:
	1. Interoperabilidad: Necesitamos que el sistema pueda ser usado en múltiples plataformas, de manera que tengamos una mayor cantidad de potenciales usuarios en el sistema. Podemos tomar la cantidad de sistemas operativos y plataformas en las cuales funciona el sistema para medir este atributo.
	2. Usabilidad: Tenemos que brindar una buena experiencia de usuario al usar el sistema. Tiene que tener una interfaz sencilla, y las acciones deben poder realizarse de forma rápida. Aquí podemos realizar encuestas a los mismos usuarios para ver su nivel de satisfacción con el sistema.
	3. Seguridad: Tenemos que asegurarnos de brindar una capa de seguridad al sistema, debido a que en los emails pueden viajar datos sensibles de los usuarios, y no queremos que el canal de comunicación sea inseguro. Se deben seguir estándares de seguridad, y se pueden realizar auditorías de forma regular para medir este atributo.


---

## Recu IS1 2C24

![](Ingeniería%20de%20Software%20I/img%20is1/Pasted%20image%2020241209141604.png)

- Las daily son un tipo de ceremonia SCRUM en las cuales el equipo se reunirá diariamente. En estas reuniones(de poca duración), cada miembro expone los objetivos cumplidos el día anterior, y también cuenta sus bloqueantes para sus tareas del día corriente. Se deben organizar para hacerse diariamente, y tienen que ser cortas(de 15 a 30 minutos). Se debe proponer también la participación de cada miembro del equipo para que esta ceremonia cumpla su objetivo.
- La retrospectiva es otro tipo de ceremonia SCRUM en la cual el equipo se junta a hacer una recapitulación del Sprint actual(que ha llegado a su fin). En estas reuniones, el equipo hace un relevamiento, y cuenta las sensaciones que tuvo durante el desarrollo del Sprint. La idea es hacerla antes de finalizar el Sprint actual, y se debe asegurar que el equipo esté completo en la reunión, para que así cada miembro exponga sus sensaciones.


![](Ingeniería%20de%20Software%20I/img%20is1/Pasted%20image%2020241209142112.png)
![](Ingeniería%20de%20Software%20I/img%20is1/Pasted%20image%2020241209142126.png)
- El estado isOn de la lampara rompe el principio de OpenClosed, debido a que si yo quiero agregar un nuevo estado para la lámpara, tengo que modificar el código fuente de la clase(está abierto a modificaciones). Aquí se puede aplicar el patrón de diseño State para guardar los estados de la lámpara. Se tendría una abstracción `LampState`, y cada estado sería una implementación de esa abstracción(por ejemplo, `LampOnState`). Con esta modificación, los métodos `turnOn` y `turnOff` de la lampara simplemente delegarían a algún método interno del estado, y si yo en un futuro quiero agregar un estado nuevo, simplemente agrego la implementación de la abstracción propuesta.
- Hay dos métodos comentados de código, no sé si eso es parte de la consigna pero no pinta nada tenerlos así...
- Comentarios innecesarios en la función `main`.
- Las llamadas a `button.press()` no vuelven a apagar la cámara...


![](Ingeniería%20de%20Software%20I/img%20is1/Pasted%20image%2020241209143139.png)

4. La vista física toma en cuenta primeramente los requisitos no funcionales del sistema tales como la disponibilidad, confiabilidad, rendimento y escalabilidad.