# Unidad 3 - Investigación de los incidentes de ciberseguridad

Recopilación de evidencias, investigación, compartir IoCs. Documentar los incidentes en un sistema de ticketing. Como enfocar una investigación de multiples sistemas afectados.

## 3.1 Inicio de la investigacion

¿Qué necesito para empezar una investigación?

- Tener un triaje y análisis previo del incidente o potencial incidente.
    - Caracterización: Responder los "5 W's":
        - Who was involved?
        - What happened?
        - When did it happen?
        - Where did it happen?
        - Why did it happen?

>[!Note]
>Ver https://en.wikipedia.org/wiki/Five_Ws

- Plantear cual es el objetivo/os de la investigación. P.e.: obtener si un atacante ha podido explotar la vulnerabilidad X.
- Recopilar todas las fuentes de información necesarias para responder a las preguntas planteadas.

## 3.2 Enfocar la investigación

Es importante centrar los esfuerzos en responder las preguntas planteadas y tomar notas de otros indicios de otros líneas que puedan surgir durante el análisis de forma colateral.

P.e.: si encuentro una actividad anómala que no está directamente relacionada con la línea de investigación que estoy tratando, lo abro como una nueva línea y se considerará posteriormente.

>[!Tip]
>Si tendemos mucho a diverger, podemos perdernos en el análisis.

## 3.3 Documentar

Documentar desde el principio. Tener un bloc de notas (cada uno el software que más le guste) e ir, al menos, copiando y pegando comandos, capturas y alguna explicación breve (sin preocuparse si está bien escrito o no). En caso de trabajar con un sistema de ticketing
- Puedes aprovechar para volcar directamente esa info en el tiquet de forma continua (sin revisar) y darle una vuelta al formato y redacción al final.
- También puedes ir copiando de tu bloc solo lo más importante en el tiquet y luego ya adjuntar el informe completo cuando lo tengas.

Las capturas y copias de comandos y consultas hechas, mejor que sobre que falten. Si luego alguna no es necesaria para el informe, mejor, se borra o se archiva y ya está.

## 3.4 Organizar y priorizar

Esta parte es fundamental. De cara a no demorar la investigación de forma indefinida, hay que saber enfocar bien el análisis sabiendo:
- Las preguntas que se quieren responder tal y como se ha indicado en el punto 2, ["Enfocar la investigación"](#32-enfocar-la-investigación).
- La información donde se que puedo encontrar la respuesta a esas preguntas. Priorizar de más probable a menos probable.
- Si se puede segmentar, involucrar a varias personas en el análisis y compartir los resultados.

La gestión de la documentación y resultados en tiempo real de una investigación no es fácil, como ya se ha nombrado se suele contar con sistemas de ticketing o similar, pero se puede hacer con documentos compartidos, un chat, un panel kanban, etc.

## 3.5 MITRE ATTACK[^1][^2][^3]

[^1]: https://ciberseguridad.com/herramientas/marco-mitre-att-ck/
[^2]: https://www.trendmicro.com/es_es/what-is/cyber-attack/mitre-attack-framework.html
[^3]: https://blog.ehcgroup.io/2021/06/04/10/00/58/11220/guia-de-uso-de-mitre-attck-para-analistas-de-amenazas/noticias-de-seguridad/ehacking/

La **matriz MITRE ATT&CK** (Adversarial Tactics, Techniques, and Common Knowledge) es una base de conocimientos que documenta tácticas y técnicas utilizadas por actores y grupos de ciberdelincuentes en el mundo real a nivel mundial. Esta matriz organiza las tácticas y técnicas en diferentes fases del ciclo de vida de un ataque, desde el acceso inicial hasta la exfiltración de datos.

### Uso de la matriz MITRE ATT&CK

1. **Modelado de amenazas**: La matriz se utiliza para identificar y categorizar las tácticas y técnicas que los atacantes pueden emplear. Esto ayuda a las organizaciones a entender mejor las posibles amenazas y a desarrollar estrategias de defensa más efectivas.
2. **Análisis forense**: Durante un análisis forense, la matriz ayuda a mapear las acciones del atacante a técnicas específicas, facilitando la identificación de cómo ocurrió el ataque y qué técnicas se utilizaron.
3. **Respuesta a incidentes**: En caso de un incidente, la matriz permite a los equipos de seguridad identificar rápidamente las tácticas y técnicas empleadas por los atacantes, lo que facilita una respuesta más rápida y efectiva.

### Cómo usar la matriz MITRE ATT&CK

1. **Identificación de tácticas y técnicas**: Utiliza la matriz para identificar las tácticas (objetivos de alto nivel) y técnicas (métodos específicos) que los atacantes podrían emplear.
2. **Mapeo de incidentes**: Durante un análisis forense, mapea las acciones observadas del atacante a las técnicas documentadas en la matriz. Esto ayuda a entender el comportamiento del atacante y a identificar posibles brechas en la seguridad.
3. **Desarrollo de defensas**: Usa la matriz para identificar y priorizar las defensas necesarias contra las técnicas más relevantes para tu organización.
4. **Evaluación continua**: La matriz se actualiza regularmente para reflejar nuevas tácticas y técnicas, por lo que es importante mantenerse al día con las actualizaciones para mejorar continuamente las estrategias de defensa.

### Ejemplo guiado

https://tryhackme.com/room/compromisedwindowsanalysis

> Joe observed some suspicious traffic (SSH Connections) to a malicious IP address from one of the employee’s (Aashir) host. Joe also observed that the connection attempts repeated after precisely one minute and were refused every time.

> Joe blocks the IP over the network and contains the host immediately. After conducting the initial investigation, Joe found that Aashir was unaware of this connection and observed a prompt on the screen after every minute. Aashir also found the built-in antivirus, Windows Defender, turned off.

Linea temporal:
- Creación tarea CnC
    - T1053.005: Scheduled Task
- Contacto por SSH en la tarea CnC
    - T1572: Command and control a través de SSH
- Subida de `cursed.rar` al sistema de la víctima
- Extracción en `Desktop\Cursed` y ejecución de `powershell.exe` y `cipher.exe` como binario no reconocido.
- No se puede recuperar el fichero ni se encuentra el hash. Se revisa la actividad en logs tras ejecutarse y se observa:
    - T1021.001: RDP
    - T1562.001: Disable or Modify Tools (disabled Defender)

## 3.6 Actividades propuestas

Se proponen las siguientes actividades interactivas de tipo teórico/práctico:
- https://tryhackme.com/room/redteamthreatintel
- https://tryhackme.com/room/unifiedkillchain
- https://tryhackme.com/r/room/servidae
- https://cyberdefenders.org/blueteam-ctf-challenges/qradar101/
- https://tryhackme.com/r/room/contiransomwarehgh
	- https://medium.com/@evamonicamijares/tryhackme-conti-ransomware-room-walkthrough-c0a75d389ae8
- https://tryhackme.com/room/dunklematerieptxc9
	- https://medium.com/@damaidec/dunkle-materie-thm-procdot-tool-analysis-on-ransomware-524878dcc745
- https://tryhackme.com/r/room/revilcorp
	- https://terguttac.medium.com/tryhackme-revil-corp-5a49b61d4c42
- Usar o conocer algun servicio de gestión de incidentes como TheHive: https://app.letsdefend.io/training/lessons/open-source-soar-thehive
