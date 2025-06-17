# Unidad 4 - Implementación de medidas de ciberseguridad (contención y erradicación)

Las medidas de ciberseguridad se pueden aplicar de forma preventiva, como lo son las explicadas en la unidad 1 con sistemas de detección y prevención, o reactivas, que ya forman parte de una fase de contención y mitigación cuando ha ocurrido un ciberataque.

## 4.1 Medidas de contención

- Son acciones que se aplican para impedir que el ataque continue libremente, evitando así la propagación y reduciendo el impacto.
- Mientras que se aplican, la investigación continua buscando aplicar nuevas contenciones necesarias o la erradicación del incidente.
- Tienen caracter temporal
- Deben ser proporcionales al ataque
- Deben ser ágiles, puesto que si no puede ser demasiado tarde ya para aplicarse, y porque se usan para ganar tiempo.
- Puede que se planteen medidas de contención drásticas, como el bloqueo de un servicio crítico. Para ello debe estar consensuado con un equipo de continuidad de negocio.
- Algunas acciones que podrían proponerse en una infraestructura profesional son:
	- Bloquear IPs, hashes u otros IoCs.
	- Bloquear usuarios o combiar contraseñas.
	- Aislar dispositivos de red, segmentos de red, oficinas, etc.
	- Aislar OUs en AD

### Pirámide del dolor

Para clasificar y entender que consecuencias tiene nuestras acciones de contención en el plan del atacante tenemos la pirámide del dolor[^1]:

![b5fd077523feb3996437e0aba3b94fdc.png](/U4%20-%20Medidas/_resources/b5fd077523feb3996437e0aba3b94fdc.png)

[^1]: https://www.securityartwork.es/2022/03/09/purple-team-why-all-the-fussii-threat-intelligence/

## 4.2 Medidas de erradicación

Una vez la investigación ya esté avanzada y se tenga con alta confianza la información del ataque y el impacto real, se podrá pensar en aplicar medidas de erradicación como lo son:
- Eliminación de cuentas de usuario creadas por el atacante.
- Eliminación de ficheros sospechosos
- Hunting de los IoCs encontrados del ataque por si se encuentran otros dispositivos o servicios vulnerados no detectados aún.
- Resolver vulnerabilidades explotadas por el atacante (CVEs, debilidades...)
- Cambios de contraseñas de usuarios administradores en caso de un compromiso del dominio. En caso de compromiso total y evidencias de Golden Ticket, será recomendable cambiar la contraseña del usuario KRBTGT.

## 4.3 Recuperación

Ya con la amenaza mitigada, las siguientes acciones van enfocadas a la recuperación del servicio a su estado habitual. Este proceso será todo lo lento que deba ser para asegurar el mayor porcenaje de éxito y habrá debido ser probado con anterioridad al incidente para no encontrarse con problemas no identificados. Entre las acciones de recuperación se encuentran:
- Deshacer las acciones de contención aplicadas ya que se ha erradicado el incidente.
- Restaurar los sistemas de backups limpios (asegurar que no contienen IoCs identificados durante la investigación).
- Auditar y monitorizar los sistemas y servicios recuperados en busca de indicadores de compromiso conocidos del incidente, o de nuevos relacionados.

Para realizar estas acciones es recomendable lo que se llaman redes limpias, grises y sucia:
- Red sucia: red infectada durante el incidente que se encuentra aislada y se usa para la investigación del incidente o para recuperación de cierta información.
- Red gris: red de prueba donde se montan backups o servicios recuperados donde se comprueban que no están infectados y pueden usarse.
- Red limpia: una vez validada la integridad y seguridad de los sistemas de la red gris, se moveran a la red limpia donde se empecerá a dar el servicio paulatinamente.

## 4.4 Actividades propuestas

Se proponen las siguientes actividades interactivas de tipo teórico/práctico.

Contención:
- https://tryhackme.com/r/room/pyramidofpainax

Todo el proceso:
- https://tryhackme.com/r/room/incidentresponseprocess
- https://tryhackme.com/r/room/irplaybooks

Reporting:
- https://tryhackme.com/r/room/dfirprocesslegalconsiderations

Mitigación (prácticas):
- https://tryhackme.com/r/room/follinamsdt
- https://tryhackme.com/r/room/joomify
- https://tryhackme.com/r/room/cactus
- https://tryhackme.com/r/room/papercut
- https://tryhackme.com/r/room/solar

### Prácticas en grupo o tutorizadas

Sobre la práctica del SIEM propuesta en la U2, automatizar el proceso de contención:
- Crear y ejecutar playbooks para autoremediación (SOAR).
