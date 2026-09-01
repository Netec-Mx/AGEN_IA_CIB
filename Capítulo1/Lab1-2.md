#  Crea agentes en el Copilot Studio integrando tus datos e IA Gen

## Objetivo de la práctica:
Al finalizar la práctica, serás capaz de:
- Crear y configurar un agente personalizado en Copilot Studio integrando datos empresariales desde SharePoint y ajustando sus respuestas mediante instrucciones específicas.
- Aplicar opciones de seguridad y autenticación para controlar el acceso y proteger la información gestionada por el agente.
- Configurar acciones automatizadas usando conectores, como el envío de correos electrónicos a través de Outlook, y establecer reglas para asegurar el flujo seguro de información.

## Diagrama del laboratorio 
El siguiente diagrama resume visualmente lo que realizarás a lo largo de la siguiente práctica. 

![diagrama1](../images/1Capitulo2Intro1.png)

## Duración aproximada:
- 35 minutos.

## Instrucciones 
La creación de agentes con Copilot Studio permite diseñar asistentes inteligentes que interactúan de forma natural con los usuarios, automatizan tareas y aprovechan el poder de la inteligencia artificial generativa. Estos agentes pueden integrarse con los datos propios de la organización, como archivos, bases de conocimiento o sitios de SharePoint, para ofrecer respuestas contextualizadas y precisas. Además, Copilot Studio ofrece controles de seguridad robustos, como la inspección de contenido, la gestión de permisos y el monitoreo de actividad, lo que garantiza que las acciones generadas por IA se mantengan dentro de los límites definidos por la organización. Gracias a su compatibilidad con conectores y herramientas externas, los agentes pueden ejecutar acciones como enviar correos, actualizar registros o activar flujos de trabajo, todo de forma segura y controlada.

En este laboratorio realizarás la creación de un agente personalizado dentro de Copilot Studio. Accederás a la plataforma, crearás un nuevo agente desde cero y explorarás las opciones de seguridad disponibles, como el control de acceso y la inspección de prompts. Luego, añadirás datos desde un sitio de SharePoint para enriquecer las respuestas del agente con información interna de la organización. También utilizarás un conector de Outlook para enviar un correo electrónico como acción generada por el agente, y configurarás una regla de seguridad que permita el acceso restringido a dichos correos, asegurando que solo usuarios autorizados puedan recibirlos. Esta práctica te permitirá comprender cómo combinar IA, datos empresariales y políticas de seguridad en un entorno real.



### Tarea 1. Crear un agente en Copilot Studio.

**Paso 1.** Desde tu navegador ingresa a [Microsoft 365 Copilot](https://m365.cloud.microsoft/) usando el siguiente link: `https://m365.cloud.microsoft/`, y usa las credenciales otorgadas por el instructor. 

![LabImage](../images/1Capitulo2Lab1.png)

---

**Paso 2.** En el menú lateral izquierdo haz clic en la opción **New agent**. Luego, escribe el siguiente prompt:

`Crea un agente que otorgue información acerca de la nómina a los usuarios del área de Recursos humanos.`

![LabImage](../images/1Capitulo2Lab4.png)

---

**Paso 3.** El copiloto generará las configuraciones básicas del agente por ti.

![LabImage](../images/1Capitulo2Lab5.png)

Si deseas, puedes modificar manualmente los datos básico de tu agente, si estás satisfecho haz clic en **Create**.

---

**Paso 4.** Cuando haya terminado, aparecerá un mensaje de confirmación, ciérralo. Ahora en los tres puntos horizontales del costado superior derecho haz clic y luego en **Copy to Copilot Studio** y luego en **Get started**.

![LabImage](../images/1Capitulo2Lab6.png)

---

**Paso 5.** Luego selecciona el entorno que tiene por nombre **Netec**.

> ⚠️**Nota:** En algunas pruebas se copió el agente a Copilot Studio, en otras, se abre un agente en blanco. Si tu caso es el último, copia y pega 

---

### Tarea 2. Configuraciones de modelos de IA y seguridad

**Paso 1.** Una vez creado el agente, en Copilot Studio puedes ajustar el modelo que puede usar. Observa los modelos de lenguaje disponibles.

![LabImage](../images/1Capitulo2Lab11.png)

---

**Paso 2.** Haz clic en los tres puntos horizontales del costado superior derecho (...) y luego en **Settings**. Navega por las opciones de seguridad que podríamos usar:

* **AI & Behavior:** **Orchestration** (Allow other agents to connect. Let other agents in your organization invoke this agent as a tool). | **Safety** Moderation level (Controls how strictly responses are filtered for unsafe content)
* **Safety & access:** **AuthN** (How users authenticate when interacting with this agent)

![LabImage](../images/1Capitulo2Lab12.png)

> No hagas modificaciones, pero discute con tu instructor y compañeros en qué aspectos implican dichas configuraciones en tus tareas de seguridad.

---

### Tarea 4. Parametrizar correctamente el agente

**Paso 1.** Usando la pestaña **Preview** prueba del agente, envíale el siguiente prompt:

`¿Qué selección de fútbol es la actual campeona del mundial?`

![LabImage](../images/1Capitulo2Lab19.png)

---

**Paso 2.** Observa la respuesta del agente. Está abierto a cualquier tipo de pregunta y cotexto. 

---

**Paso 3.** No queremos que las respuestas sean abiertas, para lograr reducir el conocimiento, debemos agregarle el nuestro. Regresa a la pestaña **Build** y fíjate que en la sección **Knowledge** o **Conocimiento** dice `Search all websites`. Haz clic en la 'x' de `Search all websites` y luego en el ícono '+'.

![LabImage](../images/1Capitulo2Lab21.png)

---

**Paso 4.** Selecciona la opción **SharePoint**.

![LabImage](../images/1Capitulo2Lab23.png)

---

> Debes crear un sitio en sharepoint. Sigue estos pasos generales, pide apoyo a tu instructor de ser necesario.
> 1. Ingresa a `https://sharepoint.microsoft.com/`
> 2. Del menú izquierdo haz clic en **Build**
> 3. Selecciona **Site** - **Standard Teams**
> 4. Haz clic en **Use template**
> 5. El nombre de tu sitio debe ser tus iniciales, por ejemplo: `jdsg` para garantizar que sea único en el tenant.
> 6. Finalmente, haz clic en **Create site**.
> 7. Cierra la ventana emergente y accede a tu nuevo sitio.
> 8. Del costado izquierdo, selecciona **Documents**.
> 9. Haz clic en **Create or upload** y selecciona **Excel Workbook**.
> 10. Cambia el nombre del documento a ```Informe de nómina```.
> 11. Vamos a tomar este archivo como ejemplo, puedes agregar la información que desees, puedes usar Copilot para que sea más rápido, o tomar los siguientes datos de ejemplo para sólo copiar y pegar en el archivo de Excel:

| Código   | Empleado          | Área               | Cargo                        | Tipo de contrato | Salario base | Horas extra | Bonificación | Total devengado | Deducciones | Neto estimado |
|----------|-------------------|--------------------|------------------------------|------------------|--------------|-------------|--------------|-----------------|-------------|---------------|
| EMP-001  | Laura Martínez    | Recursos Humanos   | Analista de Selección        | Indefinido       | $3.200.000   | $180.000    | $200.000     | $3.580.000      | $286.400    | $3.293.600    |
| EMP-002  | Carlos Rodríguez  | Finanzas           | Coordinador Contable         | Indefinido       | $5.800.000   | $0          | $500.000     | $6.300.000      | $690.000    | $5.610.000    |
| EMP-003  | Diana Gómez       | Servicio al Cliente| Asesora de Servicio          | Término fijo     | $2.600.000   | $120.000    | $0           | $2.720.000      | $217.600    | $2.502.400    |
| EMP-004  | Andrés López      | Tecnología         | Líder de Desarrollo          | Indefinido       | $8.500.000   | $0          | $1.200.000   | $9.700.000      | $1.350.000  | $8.350.000    |
| EMP-005  | Natalia Hernández | Mercadeo           | Profesional de Mercadeo      | Indefinido       | $4.200.000   | $0          | $260.000     | $4.460.000      | $401.400    | $4.058.600    |
| EMP-006  | Juan Pérez        | Operaciones        | Auxiliar de Operaciones      | Término fijo     | $2.900.000   | $90.000     | $150.000     | $3.140.000      | $251.200    | $2.888.800    |
| EMP-007  | Marcela Torres    | Ventas             | Ejecutiva Comercial          | Indefinido       | $6.700.000   | $0          | $350.000     | $7.050.000      | $775.500    | $6.274.500    |
| EMP-008  | Felipe Ramírez    | Compras            | Analista de Abastecimiento   | Obra o labor     | $3.600.000   | $140.000    | $0           | $3.740.000      | $317.900    | $3.422.100    |
| EMP-009  | Sofía Castillo    | Jurídica           | Abogada Corporativa          | Indefinido       | $7.200.000   | $0          | $400.000     | $7.600.000      | $912.000    | $6.688.000    |
| EMP-010  | Jorge Ramírez     | Logística          | Coordinador de Logística     | Término fijo     | $3.800.000   | $200.000    | $100.000     | $4.100.000      | $328.000    | $3.772.000    |
| EMP-011  | Valentina Ríos    | Innovación         | Especialista en Proyectos    | Indefinido       | $5.500.000   | $0          | $300.000     | $5.800.000      | $696.000    | $5.104.000    |
| EMP-012  | Sebastián Mora    | Tecnología         | Ingeniero de Soporte         | Obra o labor     | $3.200.000   | $150.000    | $120.000     | $3.470.000      | $278.000    | $3.192.000    |
| EMP-013  | Camila Duarte     | Ventas             | Representante Comercial      | Término fijo     | $2.800.000   | $100.000    | $80.000      | $2.980.000      | $238.400    | $2.741.600    |
| EMP-014  | Ricardo Sánchez   | Finanzas           | Analista Financiero Senior   | Indefinido       | $6.400.000   | $0          | $450.000     | $6.850.000      | $822.000    | $6.028.000    |
| EMP-015  | Andrea López      | Mercadeo           | Diseñadora Gráfica           | Obra o labor     | $3.000.000   | $80.000     | $90.000      | $3.170.000      | $254.000    | $2.916.000    |

> Guarda los datos como tabla y regresa a tu sitio de sharepoint.

![LabImage](../images/1Capitulo2Lab23.png)  

Regresa a Sharepoint, ya deberías ver el documento cargado. Ahora sólo selecciona el archivo y haz clic en **Copy link**.

**Paso 6.** En Copilot Studio en la ventana para agregar el conocimiento de sharepoint pega el link del documento que creaste antes, y luego, haz clic en el botón **Add**. Finalmente, en **Add to agent**

![LabImage](../images/1Capitulo2Lab24.png)  

---

**Paso 7.** Ahora, en la sección de **Instrucciones** busca la sección **restricciones**, **limitaciones** o algo similar, si no existe créala y agrega el siguiente texto:

```
Limitaciones:
Sólo debes contestar preguntas acerca de la nómina de la empresa, que están en el documento adjunto. Si te hacen preguntas fuera de este contexto debes contestar; "Lo siento, no puedo ayudarte con eso."
```

![LabImage](../images/1Capitulo2Lab28.png)

---

**Paso 8.** Ahora, en la pestaña *Preview**, envíale nuevamente el siguiente prompt:

`¿Qué selección de fútbol es la actual campeona del mundial?`

---

**Paso 9.** Observa la respuesta del agente. Ya no responde preguntas por fuera de contexto.

Hazle la siguiente pregunta:

`¿Cuál es el colaborador que más gana en la organización?`

> **Nota:** Si quieres validar que la respuesta sea correcta, dirigete al sitio de SharePoint antes mencionado.

---

**Paso 13.** El problema ahora es que está dando nombres propios, vamos a modificar esto en las instrucciones. 

Regresa a la pestaña de **Información general** y haz clic nuvamente en **Editar** de la sección ***Instrucciones***. 

Agrega la siguiente instrucción al inicio:

`No debes dar nombres propios de los colaboradores, esa información debe ser confidencial`.

Luego, haz clic en el botón **Guardar**.

![LabImage](../images/1Capitulo2Lab32.png)

---

**Paso 14.** En la ventana de chat de prueba del agente, envíale nuevamente el siguiente prompt:

`¿Cuál es el colaborador que más gana en la organización?`

![LabImage](../images/1Capitulo2Lab33.png)

Observa que ahora no da nombres propios.

### Tarea 5. Configurar una acción con un conector

**Paso 1.** Cambia a la pestaña **Herramientas** y haz clic en el botón **+ Agregar herramienta**.

![LabImage](../images/1Capitulo2Lab34.png)

---

**Paso 2.** Tómate un momento para ver las herramientas disponibles. Selecciona el conector **Office 365 Outlook**.

![LabImage](../images/1Capitulo2Lab35.png)

---

**Paso 3.** En la siguiente ventana aparecen todas las acciones permitidas para este conector, tómate un momento para verlas, y selecciona **Enviar correo electrónico (V2)**.

![LabImage](../images/1Capitulo2Lab36.png)

---

**Paso 4.** En la siguiente ventana haz clic en la opción **No conectado** y luego en **Crear una nueva conexión**.

![LabImage](../images/1Capitulo2Lab37.png)

---

**Paso 5.** Ahora, en la siguiente ventana haz clic en el botón **Crear**.

![LabImage](../images/1Capitulo2Lab38.png)

---

**Paso 6.** Posiblemente te solicite nuevamente realizar un proceso de autenticación, de ser así hazlo, de lo contrario para al paso siguiente.

![LabImage](../images/1Capitulo2Lab39.png)

---

**Paso 7.** Una vez autenticado, haz clic en **Agregar y configurar**.

![LabImage](../images/1Capitulo2Lab40.png)

---

**Paso 8.** Ahora tienes una nueva herramienta para el agente en cuestión. Baja a la sección ***Entradas***, y fíjate que tanto el destinatario, como el asunto y el cuerpo del correo serán elegidos por el modelo de lenguaje, si bien, es posible personalizar estos parámetros, para este ejercicio los dejaremos así. 

![LabImage](../images/1Capitulo2Lab41.png)
![LabImage](../images/1Capitulo2Lab42.png)

---

**Paso 9.** Cambia a la pestaña **Información general** y haz clic en el botón **Editar** de la sección ***Instrucciones***.

![LabImage](../images/1Capitulo2Lab43.png)

---

**Paso 10.** Agrega la siguiente instrucción al final de la que ya habías puesto manualmente, pero antes de la que ya estaba configurada:

`Si el usuario realiza una pregunta dentro del contexto del archivo de nómina, darás la respuesta acorde y preguntarás si desea que esa información se envíe por correo, de recibir una respuesta afirmativa procederás a enviarlo, de lo contrario le preguntarás si hay algo más en lo que desea que le ayudes.`

Luego, haz clic en **Guardar**.

![LabImage](../images/1Capitulo2Lab44.png)

---

**Paso 11.** Nuevamente en la ventana de chat de prueba del agente, envíale el siguiente prompt:

`¿Cuál es el área que en promedio gana menos?`

Luego, dile que sí quieres que te envíe esta información por correo. 

![LabImage](../images/1Capitulo2Lab45.png)

---

**Paso 12.** Revisa el mensaje de advertencia en la solicitud de autorización, haz clic en **Permitir**.

![LabImage](../images/1Capitulo2Lab46.png)

---

**Paso 13.** Ahora, revisa el correo de la cuenta con la que te autenticastes en el conector, deberías tener un nuevo correo con la información solicitada.

![LabImage](../images/1Capitulo2Lab47.png)
![LabImage](../images/1Capitulo2Lab48.png)
![LabImage](../images/1Capitulo2Lab49.png)

---

**Paso 14.** Este error 550 5.7.708 indica que el servidor de correo de Microsoft rechazó el mensaje porque no acepta tráfico desde la dirección IP desde la que se intentó enviar el correo. Específicamente, significa:
* "Access denied, traffic not accepted from this IP": El servidor considera que la IP tiene baja reputación o no está autorizada para enviar correos a través de Exchange Online.
* Es común en clientes nuevos, especialmente si estás usando una suscripción de prueba de Microsoft 365 o si el servidor de envío no está correctamente configurado.
* También puede ocurrir si estás enviando correos desde una aplicación o servicio externo (como Postman, Graph API, o un servidor SMTP personalizado) sin los permisos o licencias adecuadas.

**Paso 15.** Para intentar resolver el problema ingresaremos a [Exchange Admin Center](https://admin.exchange.microsoft.com/) usando el siguiente link: `https://admin.exchange.microsoft.com/`. Una vez allí, seleccionarás **Mail flow** y luego **Rules**.

![LabImage](../images/1Capitulo2Lab50.png)

---

**Paso 16.** Haz clic en el botón **+ Add a rule** y selecciona la opción **Create a new rule**.

![LabImage](../images/1Capitulo2Lab51.png)

---

**Paso 17.** En la ventana que aparece, configura los siguientes parámetros

* **Name:** `Permitir IP Confiable Copilot Studio`.
**Apply this rule if...**: `The sender` -> `is external/internal` -> `InOrgaization`.

* Haz clic en And para agregar otro parámetro que deberá quedar así: `The sender` -> `address matches any of these text pattern` -> ***el correo de tu usuario en el lab***.

* **Do the following...**: `Modify the message properties` -> `Set the Spam Confidence Level (SCL)` -> `Bypass spam filtering`

![LabImage](../images/1Capitulo2Lab52.png)

Luego, haz clic en el botón **Next**.

---

**Paso 18.** En la siguiente ventana, haz clic en el botón **Next**.

![LabImage](../images/1Capitulo2Lab53.png)

---

**Paso 19.** En la siguiente ventana, haz clic en el botón **Finish**.

![LabImage](../images/1Capitulo2Lab54.png)

---

**Paso 20.** Regresa a la ventana de chat de prueba del agente, envíale nuevamente el siguiente prompt:

`¿Cuál es el área que en promedio gana más?`

Luego, dile que sí quieres que te envíe esta información por correo.

![LabImage](../images/1Capitulo2Lab55.png)

### Resultado esperado. 

Revisa nuevamente el correo de la cuenta con la que te autenticastes en el conector, deberías tener un nuevo correo con la información solicitada.

**NOTA IMPORTANTE:** ***Es normal que si haces nuevamente la prueba rebote el correo.***

![LabImage](../images/1Capitulo2Lab56.png)

