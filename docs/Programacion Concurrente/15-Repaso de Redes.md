# Repaso de [[Redes/Redes|Redes]]


!!! warning "Tipos de servicio ofrecidos por las Capas"
- Sin conexión: Los datos se envían al receptor y no hay control de flujo ni de errores.
- Sin conexión con ACK: Por cada dato recibido, el receptor envía un acuse de recibo conocido por ACK.
- Con conexión: Three-way Handshake. Hay establecimiento de la conexión, intercambio de datos y cierre de la conexión. Hay control de flujo y control de errores.


## Modelo OSI de la ISO

![](Programación%20Concurrente/img%20concu/Pasted%20image%2020241215101041.png)


!!! note "Capa Física"
> Se encarga de la transmisión de datos en forma de señales (eléctricas, ópticas o electromagnéticas) a través del medio físico, definiendo las características del hardware de la red.
> - Define estándares para conectores, cables, voltajes y modulaciones, asegurando que los dispositivos puedan conectarse físicamente y transmitir bits.


!!! note "Capa de Enlace"
> Garantiza la transferencia confiable de datos entre dispositivos directamente conectados en una red.
> - Divide los datos en tramas (frames), detecta y corrige errores, y controla el acceso al medio compartido mediante direcciones físicas como las MAC.


!!! note "Capa de Red"
> Proporciona el enrutamiento y la entrega de datos entre redes diferentes, asegurando que los paquetes lleguen al dispositivo destino.
> - Utiliza direcciones lógicas (IP), selecciona rutas óptimas y gestiona la congestión de tráfico en la red.


!!! note "Capa de Transporte"
> Asegura la comunicación confiable entre los extremos de la red, garantizando la entrega completa y en orden de los datos.
> - Controla la fragmentación en segmentos, maneja retransmisiones y utiliza protocolos como TCP (fiable) o UDP (rápido).


!!! note "Capa de Sesión"
> Administra la comunicación entre aplicaciones, estableciendo, manteniendo y cerrando sesiones de forma ordenada.
> - Coordina el inicio y fin de las sesiones, sincroniza la transmisión de datos y permite la recuperación en caso de fallos.


!!! note "Capa de Presentación"
> Traduce los datos al formato requerido por las aplicaciones, asegurando que puedan interpretarse correctamente.
> - Maneja la codificación, compresión y cifrado de datos para que sean comprensibles y seguros.


!!! note "Capa de Aplicación"
> Proporciona servicios directamente a las aplicaciones del usuario, facilitando el acceso a la red.
> - Incluye protocolos como HTTP, FTP y SMTP, que soportan funciones como transferencia de archivos, correo electrónico y navegación web.
