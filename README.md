# AEE. Bitácora III. Conexiones Empresariales Taller Técnico: Operación Escudo

# Fase de Investigación: Comprendiendo el corazón del sistema

### Anatomía de Syslog

El estándar **syslog** se refiere a las **bitácoras o registros del sistema** que almacenan información cronológica sobre eventos y errores.  
El archivo principal donde se recogen estos registros es /var/log/syslog.  
Es la herramienta fundamental para el diagnóstico del sistema. Si algún componente falla (como la red, el arranque o un programa específico), la respuesta y los detalles del error suelen encontrarse documentados dentro de este archivo. 

## Clasificación de los eventos cruzando dos variables:

1. **Facilidad (Facility):** Define la **categoría o el origen** del mensaje (quién genera el evento). Algunos ejemplos comunes incluyen:  
   * `kern`: Mensajes del núcleo (kernel).  
   * `auth` o `authpriv`: Eventos relacionados con la seguridad y autenticación.  
   * `mail`: Eventos del sistema de correo.  
   * `cron`: Mensajes del programador de tareas.  
   * `daemon`: Otros servicios del sistema.  
   * `local0`\-`local7`: Reservados para aplicaciones personalizadas del usuario.  
2. **Prioridad o Severidad (Priority/Severity):** Define la **importancia o urgencia** del evento. El estándar define ocho niveles (del 0 al 7):  
   * `0 (emerg)`: Emergencia, el sistema es inoperable.  
   * `1 (alert)`: Alerta, se requiere acción inmediata.  
   * `2 (crit)`: Condición crítica.  
   * `3 (err)`: Error.  
   * `4 (warning)`: Advertencia.  
   * `5 (notice)`: Condición normal pero significativa.  
   * `6 (info)`: Mensaje informativo.  
   * `7 (debug)`: Mensajes de depuración.

**Cómo se cruzan:** El sistema utiliza un sistema de **selectores** (generalmente configurados en archivos como `/etc/rsyslog.conf`) con el formato facilidad.prioridad. Esto permite al administrador decidir qué hacer con cada tipo de mensaje. Por ejemplo:

* `mail.err /var/log/mail.err`: Envía solo los errores de correo a un archivo específico.  
* `auth.* /var/log/auth.log`: Registra todos los niveles de severidad de los eventos de autenticación.  
* `*.info;mail.none /var/log/syslog`: Registra información de todos los servicios excepto del correo en el archivo `syslog`.  
  


### ¿Por qué es una negligencia grave que el archivo */var/log/auth.log* tenga permisos de lectura para usuarios no privilegiados?

Debido a que vulnera el pilar de la Confidencialidad dentro de la tríada de seguridad CID (Confidencialidad, Integridad y Disponibilidad).

### ¿Qué información específica (como PIDs, nombres de usuario o direcciones IP) diferencia un intento fallido de conexión remota *SSH* de un simple fallo de contraseña de un usuario local frente a la pantalla?

La dirección IP o computador remoto al intentar tener conexión mediante SSH.  
El identificador de proceso (PID) .  
El nombre de usuario.

### Cumplimiento y Log Management.

Las ventajas vitales que ofrecen enviar y custodiar logs en un servidor externo en lugar de mantenerlos dispersos son los siguientes:

* Integridad de las evidencias: si hay un ataque, se pueden modificar o borrar los logs locales para ocultar el rastro pero al enviarlos a un servidor externo inmediatamente se asegura que los logs son inalterables.  
* Cumplimiento de la notificación de brechas: el RGPD\[1\] te exige notificar las brechas de seguridad en un plazo máximo de 72 horas. Tener los logs centralizados permite tener un análisis rápido, permitiendo detectar intrusos a tiempo real.  
* Protección contra "Puntos Únicos de Fallo": Si el servidor de origen es cifrado, los logs locales se pierden. Custodiar los registros en una ubicación externa asegura la continuidad y disponibilidad de la información necesaria para investigar qué datos personales fueron afectados.  
* Auditoría y Análisis de Comportamiento: Centralizar facilita la búsqueda y el análisis holístico, permitiendo monitorizar el acceso a datos sensibles (datos especialmente protegidos por el RGPD) y detectar patrones sospechosos.

\[1\] RGPD: Reglamento General de Protección de Datos. Normativa europea que regula cómo las empresas recopilan, tratan y almacenan datos personales de los ciudadanos de la UE.

# Fuentes

F. Ismael, "NotebookLM Sistemas Informaticos", Frias, . \[Online\]. Available: https://notebooklm.google.com/notebook/876507f1-786e-44f3-ba78-112dc749934c. \[Accessed: 04-17-2026\].  
F. Ismael, "Gestion centralizada LOGS", Frias, . \[Online\]. Available: https://cibersafety.com/gestion-centralizada-logs-seguridad-eficiencia/. \[Accessed: 04-17-2026\].  
F. Ismael, "Gestion centralizada LOGS", Frias, . \[Online\]. Available: https://www.aepd.es/preguntas-frecuentes/2-tus-obligaciones-como-responsable-del-tratamiento/4-los-principios-del-tratamiento/FAQ-0207-que-principios-debo-cumplir\#:\~:text=El%20tratamiento%20de%20datos%20debe,Licitud%2C%20transparencia%20y%20lealtad.. \[Accessed: 04-17-2026\].