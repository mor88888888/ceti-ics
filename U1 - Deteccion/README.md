# Unidad 1 - Detección y documentación de incidentes de ciberseguridad

Para poder afrontar de forma eficaz incidentes de seguridad deberemos contar principalmente con personas, procedimientos de actuación y la tecnología necesaria. Las tareas a realizar por el equipo para prepararse de cara a un incidente son:
- Plan de gestión de incidentes. Procedimientos de actuación y respuesta.
- Política de seguridad de la información.
- Establecimiento del equipo de respuesta ante incidentes de seguridad.
- Definición de la taxonomía de incidentes de seguridad.
- Plan de intercambio de información y comunicación con terceros.
- Formación permanente del equipo humano de respuesta ante incidentes.

Además de otras tareas que se tratarán en posteriores unidades como:
- Implantación y mantenimiento de los elementos de monitorización de eventos de seguridad.
- Simulacros del plan de gestión de incidentes.
- Concienciación y formación sobre la gestión de incidentes.

## 1.1 Establecer un equipo de respuesta

Diferencias entre SOC y CSIRT:

![e0e79279feb06cd6721dccfbf89f5d89.png](/U1%20-%20Deteccion/_resources/8acf7625a4b342a2aefefdbe91c64720)[^1]

Organización genérica en un SOC:

![53fa7c2ad062f92177841710e9b081cf.png](/U1%20-%20Deteccion/_resources/a8d51daf933349d2bdab89b6b99924c0)[^2]

[^1]: IMPLANTACIÓN SIEM HP ARCSIGHT EXPRESS (Universitat Politècnica de València)
[^2]: https://www.incibe.es/incibe-cert/blog/respondiendo-incidentes-industriales-soc-ot

Los equipos de respuesta ante incidentes pueden estar:
- Centralizados: cuando sólo hay un equipo que forma la capacidad de respuesta dentro de la empresa
- Distribuidos: hay varios equipos distribuidos por áreas, por situación geográfica, etc.
- Híbridos: una mezcla de los anteriores

Características del EQUIPO HUMANO:
- Debe tener un conocimiento técnico especializado
- Debe ser multidisciplinar
- Debe saber trabajar bajo presión
- Debe aprender continuamente
- Debe dar respuesta a toda la compañía
- Debe tener una capacidad de respuesta 24/7
- Puede pertenecer a la empresa, estar externalizado, o mixto

El equipo de respuesta ante incidentes debe estar formado en, al menos:
- La infraestructura empresarial (sistemas)
- Tecnologías utilizadas (sistemas y programación)
- Analisis de seguridad y forense (defensa)
- Arquitectura de ciberseguridad (defensa)
- Técnicas de ataque conocidas (ataque)
- Búsqueda de información en fuentes abiertas (ciberinteligencia).

## 1.2 Taxonomía de incidentes de ciberseguridad

![44482d3509c55c6b4e634fa33474ae46.png](/U1%20-%20Deteccion/_resources/7fcd4d7cd8784348af160a5bdb6ba8e0)[^3]

[^3]: Esquema sobre como clasificar incidentes en funcion de la peligrosidad y el posible impacto.

Clasificación de incidentes según el CCN-STIC-817:
- Contenido abusivo
- Contenido dañino
- Obtención de información
- Intento de intrusión
- Intrusión
- Disponibilidad
- Compromiso de la información
- Fraude
- Vulnerable
- Otros

Clasificación del riesgo:

![ff9c3a1e104cc71477298eb43fc03d95.png](/U1%20-%20Deteccion/_resources/dec1c284a1474c5c807dfcecc4fd8748)[^4]

[^4]: https://www.coordinacae.com/blog/matriz-de-riesgos/

Alerta vs Evento vs Incidente:
- Alerta: cualquier aviso de seguridad proviniente de los sistemas de seguridad.
- Evento: conocimiento de un posible compromiso de la seguridad, o un suceso confirmado de bajo impacto.
- Incidente: confirmación del compromiso parcial o total de la seguridad de medio o alto impacto.

## 1.3 Procedimientos

Objetivos: establecer las directrices generales para la gestión de incidentes de seguridad, para prevenir y mitigar el impacto de las mismas.
- Propósito y objetivos del procedimiento
- Alcance
- Definición de incidente de seguridad y consecuencias dentro de la organización
- Criterios de clasificación para un incidente de seguridad
- Criterios para evaluar la criticidad de un incidente
- Estructura organizativa, delimitación de roles, responsabilidades y contactos

## 1.4 Intercambios de información

En algunos casos es necesaria la comunicación de incidentes a terceros: autoridades competentes, CSIRT, afectados...

Debes conocer a quien informar para cada caso de incidente y dependiendo del riesgo o el impacto confirmado.

> “Si la brecha de seguridad constituye un riesgo para los derechos y las libertades de las personas se debe notificar ante la AEPD en un plazo máximo de 72 horas desde que se tenga constancia a través del enlace habilitado en la Sede electrónica.”
> Ver https://www.aepd.es/prensa-y-comunicacion/blog/brechas-de-seguridad-de-datos-personales-que-son-y-como-actuar

La colaboración e intercambio de información voluntaria entre empresas u organizaciones puede ayudar a mejorar los tiempos de respuesta frente a incidentes. Los acuerdos de este tipo deben cumplir una serie de requisitos como:
- Confianza: acordar el tipo de información, establecer niveles de difusión y clasificación
- Estandarización: estándares y acuerdos
- Accesibilidad y calidad de los datos: información precisa, actualizada y compartida con agilidad
- Tratamiento que se le da a la información:
- Registro seguro de la información que se comparte
- Acceso adecuado al nivel
- Canales de información seguros

### Qué información compartir

IoCs:
- Son evidencias específicas y concretas que demuestran que un sistema o red ha sido comprometido.
- Se basan en firmas y patrones conocidos asociados con virus, malware u otras amenazas que suelen figurar en bases de datos públicas.

![da15da7a032b54ee2bbf7ee4c29dc2a7.png](/U1%20-%20Deteccion/_resources/3e583320ab1a4847a008c22345afda13)[^5]

[^5]: https://www.micromouse.com/2022/11/24/indicadores-de-compromiso-ioc-el-termometro-de-tus-sistemas/

IoAs:
1. Son señales que indican una actividad potencialmente maliciosa en curso o un patrón de comportamientos que podrían indicar un ataque en sus fases tempranas.
2. No se basan en firmas conocidas, sino que analizan las tácticas, técnicas y patrones de comportamiento típicas de los atacantes.
3. Constituyen cualquier evidencia física o digital que indica que es probable que ocurra un ciberataque.

## 1.5 Actividades propuestas

Se proponen los siguientes ejercicios teóricos interactivos:
- https://tryhackme.com/r/room/socfundamentals
- https://tryhackme.com/r/room/introtoirandim
- https://tryhackme.com/r/room/preparation
