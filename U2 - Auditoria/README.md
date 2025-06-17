# Unidad 2 - Auditoría de incidentes de ciberseguridad

El objetivo de esta unidad es entender como de detecta, clasifica y analiza un incidente al poco de haber ocurrido. Para ello, hay que entender como funciona una red empresarial (propuesto en la unidad 0) y ver en qué puntos podemos detectarlo:

## 2.1 Elemenos de detección/contención en una infraestructura empresarial

Seguridad perimetral de una web[^1]:

![a5c8af34a3c98be09fa2196d745d05ef.png](/U2%20-%20Auditoria/_resources/a5c8af34a3c98be09fa2196d745d05ef.png)

[^1]: https://cheatsheetseries.owasp.org/cheatsheets/Network_Segmentation_Cheat_Sheet.html

Diagrama básico de funcionamiento lógico de la DMZ[^2]:

![c6c402cdc7ed0f95b9397d0f50a338a6.png](/U2%20-%20Auditoria/_resources/c6c402cdc7ed0f95b9397d0f50a338a6.png)

[^2]: https://www.techtarget.com/searchsecurity/definition/screened-subnet

Seguridad endpoint[^3]:

![940e812112d7f839116a15112b25a0a1.png](/U2%20-%20Auditoria/_resources/940e812112d7f839116a15112b25a0a1.png)

[^3]: https://www.varonis.com/blog/endpoint-detection-and-response-edr

Herramientas de ciberinteligencia[^4]:

![0625f2b58e0d01c3f0a6adc19dc75fc0.png](/U2%20-%20Auditoria/_resources/0625f2b58e0d01c3f0a6adc19dc75fc0.png)

[^4]: https://www.visiumtechnologies.com/mitre-attack/

Colector y correlador de logs (SIEM), cómo trabaja[^5]:

![84990c246c4a6c551cec292edb6705e9.png](/U2%20-%20Auditoria/_resources/84990c246c4a6c551cec292edb6705e9.png)

[^5]: https://www.sentinelone.com/cybersecurity-101/data-and-ai/ciem-vs-siem/

SIEM, para qué lo necesito[^6]:

![e76ccbbab040c4abd288c462ee7e8844.png](/U2%20-%20Auditoria/_resources/e76ccbbab040c4abd288c462ee7e8844.png)

[^6]: https://www.cloud9data.com/managed-siem-benefits-providers-best-practices/

## 2.2 Cómo gestionar los logs en un SIEM

1. Diseñar un caso de uso para una anomalía, TTP, etc.
2. Determinar que fuentes de logs necesito y que campos de estos logs para poder detectar el caso de uso.
3. Si no los tengo ya, integro la fuente nueva, o los campos que no tenía.
4. Activo la alerta con algún tipo de tag (test) durante un tiempo donde:
5. Fuerzo el caso de uso para ver si lo detecta (purple team).
6. Monitorizo si salta algun Falso Positivo derivado de este nuevo caso de uso.
7. Monitorizo si hay un impacto excesivo en el rendimiento del SIEM tras activarla.
8. Tras el paso anterior y la confirmación de que todo ha ido bien, activo la alerta junto con el resto.
9. Monitorizo que los equipos estan bien dimensionados para responder a la cantidad de alertas que saltan, y para seguir creando nuevas.

Cómo NO hacerlo:
- Por cada sistema que me encuentro en mi infraestructura, vuelvo todos los logs en el SIEM para tenerlos disponibles para búsquedas o para ver si se me ocurre alguna alerta que generar.
	- Para esto está el syslog, sistemas de datalake, etc.
- Por cada fuente que integro, no me preocupo de indexar, mapear y normalizar los campos de los logs.
- No me preocupo de si voy a usar unos campos u otros en el log y vuelco la fuente de datos entera.
- Impacto considerablemente en el rendimiento del SIEM con la integración de nuevas fuentes y no hago nada para resolverlo.
- Creo más alertas de la que mi equipo puede gestionar.

## 2.3 Primera respuesta y funcionamiento de un SOC

Tras detectar un posible problema de seguridad (alerta), el equipo de SOC N1 hará un primer "triaje" del suceso con la información procedimentada a recopilar. Ejemplo del NIST de que elementos recoger sobre una alerta[^7]:

![1de385272f51598716c2fe5746dbf000.png](/U2%20-%20Auditoria/_resources/1de385272f51598716c2fe5746dbf000.png)

[^7]: NIST 800-61 rev2 (en) - https://nvlpubs.nist.gov/nistpubs/specialpublications/nist.sp.800-61r2.pdf

Es posible que incluso se haga un análisis provisional por parte del analista N1 y se apliquen contenciones básicas ya previstas. Ejemplo de playbook[^8]:

![9ba6fd353a6844e7127928161382dcce.png](/U2%20-%20Auditoria/_resources/9ba6fd353a6844e7127928161382dcce.png)

[^8]: https://swimlane.com/blog/incident-response-playbook/

Luego se escalará a N2 en caso de ser necesarias más acciones como la investigación de un posible evento/incidente o medidas de contención no contempladas en los procedimientos del tipo de alerta gestionada.

En caso de requerir un especialista en un conocimiento concreto, una gestión de un incidente grave de ciberseguridad, y algunas otras funciones; se escalará el caso al N3.

### El analista N1

Responsabilidades:
- Ejecuta procedimientos para determinar la peligrosidad de una alerta y generar un primer triaje de información.
- Descartan todos los falsos positivos y alertas de ataques sin impacto en función de esos procedimientos.
- Cuando las fuentes no generan alertas de forma directa o no están integradas con el SIEM, se puede procedimentar una revisión de logs con ciertos filtros directamente en la fuente.
- Sus tareas son automatizables cuando la madurez de los procesos y procedimientos están avanzadas.

Qué necesita:
- Procedimientos para cada tipo de ataque o situación, incluso para cuando no está contemplado el tipo de ataque.
- Tecnologías de detección eficaces para hacer saltar la alerta.
- Capacidad de obtener y analizar los logs necesarios para cada tipo de ataque.
- Un sistema de gestión de alertas y casos para tener la documentación y estado de cada suceso en un único lugar.
- Base de conocimiento en ciberseguridad.

### El analista N2

Responsabilidaes:
- No suele hacer uso de procedimientos, aunque sí que puede disponer de guías y plantillas.
- Ayudan a N1 en caso de duda con el tratamiento de las alertas.
- Diseñan y mejoran procedimientos para N1.
- Gestionan casos relevantes sin impacto y eventos, y participan en incidentes.
- Colaboran con otros equipos para la mejora del proceso de detección.

### El analista N3

Perfiles senior o expertos en una materia, por lo que habitualmente estan especializados.

Se conocen roles como:
- Treath Hunting: búsqueda proactiva de amenazas. Sus búsquedas NO se basan en alertas generadas, sino en indicadores de ataques. Buscan indicios como:
	- IoCs de ataques ocurridos en la organización o fuera de ella.
	- TTPs conocidas de atacantes que potencialmente podrían tener como objetivo la organización. Ver https://attack.mitre.org/.
- Treath Intelligence: búsqueda proactiva de potenciales amenazas provenientes del exterior.
	- Colaboran con información que necesita el equipo de TH para sus búsquedas en fuentes abiertas. P.e. Alienvault, MISP, MITRE ATTACK...
	- Vigilancia digital: monitorizan actividad pública sobre la organización en busca de posibles amenazas contra la organización.
		- Fraude.
		- Cybersquatting.
		- Subplantación de webs o apps.
		- Leaks de información.
		- Estudio reputacional de la organización.
	- Modelado de ciberamenazas:
		- Obtienen más información que los IoCs del ataque sufrido en cuestión.
		- Sacan TTPs que puedan usar en siguientes fases de ataque.
- Experto DFIR: especialistas en forense y respuesta ante incidentes.
	- Actuan en casos con un impacto ya reconocido.
- Risk assesment: gestión de vulnerabilidades y ciclos de parcheo.
	- Útil para prevenir explotaciones, o para conocer las posibles debilidades que un atacante ya dentro de la infraestructura ha utilizado o puede utilizar.
- Cybersecurity Architect: expertos en sistemas de detección y contención, y/o del SIEM. Necesarios para el mantenimiento de los sistemas, y para conocer qué medidas de contención o mitigación son posibles durante un incidente.

## 2.4 Actividades propuestas

Se proponen las siguientes actividades interactivas de tipo teórico/práctico:

Logs:
- https://tryhackme.com/r/room/identificationandscoping
- https://tryhackme.com/r/room/linuxincidentsurface
- https://tryhackme.com/r/room/introtologanalysis
- https://tryhackme.com/r/room/introtologs
- https://tryhackme.com/r/room/logoperations
- https://tryhackme.com/r/room/introtosiem

Phising:
- https://tryhackme.com/r/room/phishingemails1tryoe
- https://tryhackme.com/r/room/phishingemails2rytmuv
- Listar tipos de fraudes (primeros 10-15 min), ejemplo fraude del ceo (ultimos 8 min): https://www.youtube.com/watch?v=oNLa14NAABs&t=446

Detection engineering:
- https://tryhackme.com/r/room/introtodetectionengineering
- https://tryhackme.com/r/room/introtoendpointsecurity
- https://tryhackme.com/r/room/introtoav
- https://tryhackme.com/r/room/snort

SIEM:
- https://tryhackme.com/r/room/splunkexploringspl
- https://tryhackme.com/r/room/wazuhct

TI:
- https://tryhackme.com/room/cyberthreatintel
- https://tryhackme.com/r/room/threatintelligenceforsoc
- https://cyberdefenders.org/blueteam-ctf-challenges/3cx-supply-chain/
- https://cyberdefenders.org/blueteam-ctf-challenges/red-stealer/

TH:
- https://tryhackme.com/r/room/introductiontothreathunting
- https://tryhackme.com/r/room/threathuntingwithyara
- https://tryhackme.com/r/room/threathuntingfoothold

SOC Simulator - realizar tantas alertas como se tenga tiempo o se desee:
- https://app.letsdefend.io/monitoring
- https://tryhackme.com/soc-sim

### Prácticas en grupo o tutorizadas

- Montar un SIEM con logs integrados (por ejemplo access.log, auth.log, winevt...) y generar alertas de correlación propias. P.e. https://cylum.tech/articulos/crea-tu-propio-soc-con-tecnologia-open-source/
