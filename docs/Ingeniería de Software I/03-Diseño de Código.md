# Diseño de Código

![](Ingeniería%20de%20Software%20I/img%20is1/Pasted%20image%2020240925150417.png)



> [!WARNING] ¿Por qué necesitamos un buen diseño?
> 1. Para manejar el cambio.
> 2. Para tener un delivery rápido.
> 3. Para lidiar con la complejidad.
> Siguiendo los principios [SOLID](04-SOLID.md) se puede lograr un buen diseño.

## Buenas Prácticas
- Nombres significativos y pronunciables.
- Preferir nombres claros a comentarios.
- Usar nombres que revelen su intención.
- No dejar valores fijos, usar constantes con nombres claros.
- Funciones/Métodos:
	- Deberían tener menos de 8 líneas aprox.
	- Hacer una sola cosa -> [Single Responsibility Principle](04-SOLID.md).
	- Un solo nivel de abstracción por función.
	- Leer de arriba hacia abajo.
	- DRY Principle(Don't Repeat Yourself).
	- The Boy Scout Rule.
	- The Principle of Least Surprise.