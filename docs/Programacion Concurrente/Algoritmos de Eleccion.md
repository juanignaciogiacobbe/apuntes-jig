
!!! warning "Introducción y algunas suposiciones"
> Varios algoritmos requieren de un coordinador con un rol especial -> En general, no es importante cuál es el proceso, sino que debe cubrirse el rol.
> - Se busca que cualquier Host tenga la capacidad de ser el líder -> Si un líder se cae, queremos que algún otro Host pueda tomar su rol.
> - Se asume que todos los procesos tienen un ID único, se ejecuta un proceso por máquina y conocen el número de los demás procesos.
> - Cuando la elección comienza, concluye con un elegido.

# Algoritmo Bully
- Cuando un proceso P nota que el coordinador no responde, inicia el proceso de elección:
	1. P envía el mensaje ELECTION a todos los procesos que tengan número mayor.
	2. Si nadie responde, P gana la elección y es el nuevo coordinador.
	3. Si contesta algún proceso con número mayor, éste continúa con el proceso y P finaliza.
	4. El nuevo coordinador se anuncia con un mensaje COORDINATOR.
	5. Siempre gana el proceso con mayor número.

![[Programacion Concurrente/img concu/Pasted image 20241029083312.png]]

# Algoritmo Ring
1. Los procesos están ordenados lógicamente: cada uno conoce a su sucesor.
2. Cuando un proceso nota que el coordinador falló, arma un mensaje ELECTION que contiene su número de proceso y lo envía al sucesor.
3. El proceso que recibe el mensaje, agrega su número de proceso a la lista dentro del mensaje y lo envía al sucesor.
4. Cuando el proceso original recibe el mensaje, lo cambia a COORDINATOR y lo envía. El nuevo coordinador es el proceso de mayor número de la lista. La lista se mantiene para informar el nuevo anillo.
5. Cuando este mensaje finaliza la circulación, se elimina del anillo.

![[Programacion Concurrente/img concu/Pasted image 20241029083807.png]]