# Guion de presentacion — AI Reports R9K

**Duracion objetivo:** 11:30 min · Rango valido: 10:00 – 13:00

---

## Control de tiempo (cronometro en pantalla)

| Checkpoint | Minuto | Donde deberias estar |
|---|---|---|
| 1 | 3:00 | Entre S6 y S7 |
| 2 | 6:00 | Entre S11 y S13 |
| 3 | 9:00 | Entre S19 y S21 |

Si vas lento: recorta los reportes S14-S17 a 10 segundos cada uno.
Si vas rapido: amplia S7 y S19 con una frase extra de valor tecnico.

---

## Guion por diapositiva

---

### S1 — Portada `(~0:40)`

> "Buenas tardes a todos. Soy Alba Mora de la Sen, de Siemens Mobility.
> Hoy voy a presentar una PoC de analitica operativa asistida por IA:
> una plataforma que permite a operarios de centros de control consultar datos operativos
> en lenguaje natural y generar reportes tecnicos, sin necesidad de saber SQL
> ni depender de un especialista."

---

### S2 — Indice `(~0:30)`

> "La presentacion sigue este orden: primero explico el problema que resuelve,
> despues las capacidades y la tecnologia, luego la arquitectura y los tres flujos principales,
> y cerramos con validacion, resumen y preguntas tecnicas.
> En total, unos doce minutos."

---

### S3 — Problema, objetivo y alcance `(~1:00)`

> "El punto de partida es este: los centros de control registran datos operativos en tiempo real,
> trayectos, incidencias, estados por linea, en bases de datos internas.
> Pero los operarios no escriben SQL, y eso significa que para cualquier consulta
> tienen que esperar a un especialista.
>
> El objetivo de esta PoC es eliminar ese cuello de botella:
> que cualquier operario pueda preguntar en lenguaje natural, obtener datos al momento
> y exportar un reporte sin intermediarios.
> Tambien cubre el acceso a manuales tecnicos, que hoy es lento y poco trazable.
>
> Nota importante: este proyecto parte de una aplicacion base existente.
> Mi trabajo fue la extension funcional, la integracion y la validacion tecnica,
> no el desarrollo desde cero."

---

### S4 — Capacidades funcionales `(~0:55)`

> "La solucion tiene tres capacidades principales.
>
> Primero, el Chat de datos: el usuario escribe o habla en lenguaje natural,
> y la plataforma genera y ejecuta SQL de forma segura, solo en modo lectura.
>
> Segundo, el Report Builder: desde esos datos el usuario puede construir
> un reporte tecnico con visualizaciones y exportarlo a PDF o CSV.
>
> Y tercero, el Manuals Chat: un chat sobre la documentacion tecnica del software
> del centro de control, usando RAG con n8n, incluyendo entrada por voz."

---

### S5 — Interfaz visual `(~0:35)`

> "Esta es la interfaz principal: Rail9000 Chat.
> Un flujo unico donde el usuario hace su pregunta arriba,
> recibe la tabla de resultados con su narrativa explicativa,
> y desde ahi puede pasar directamente al Report Builder.
> Todo en una sola pantalla, sin fricciones."

---

### S6 — Tecnologias usadas `(~0:55)`

> "En cuanto a tecnologia, hay tres bloques.
>
> El frontend esta en Python con Streamlit, que nos permitio iterar rapido
> manteniendo una interfaz limpia y funcional.
>
> La capa de IA combina LangChain como framework de agentes,
> Azure OpenAI como modelo principal, Ollama para ejecucion local
> y sqlglot para validacion del SQL generado. La base de datos es PostgreSQL.
>
> Y para integracion y despliegue: n8n orquesta el pipeline RAG,
> Azure EntraID y Graph API gestionan autenticacion corporativa,
> y Docker con Kubernetes son la base del despliegue."

---

### S7 — Arquitectura por capas `(~0:55)`

> "Esta vista de arquitectura es la que explica por que la PoC puede evolucionar
> sin romperse.
>
> Tenemos cinco capas desacopladas: presentacion en Streamlit,
> logica de aplicacion, capa de IA con los agentes y prompts,
> capa de datos con PostgreSQL y las integraciones externas,
> e infraestructura con Docker y Kubernetes.
>
> Esa separacion nos da control: si cambia el modelo de IA o la base de datos,
> no afecta a la interfaz. Es la diferencia entre una PoC frágil
> y una base tecnica lista para produccion."

---

### S8 — Chat de datos: flujo `(~0:45)`

> "Aqui vemos el flujo del chat de datos paso a paso.
>
> El usuario hace una pregunta en lenguaje natural.
> El LLM genera el SQL correspondiente.
> Ese SQL pasa por una validacion de seguridad: solo SELECT, sin escritura.
> Se ejecuta en PostgreSQL y el resultado vuelve como tabla.
> Finalmente, el LLM genera una narrativa que resume los datos en lenguaje natural.
>
> El usuario en ningun momento ve el SQL, solo la respuesta."

---

### S9 — Resultado: tabla de datos `(~0:30)`

> "Este es un ejemplo real de salida.
> La pregunta es en lenguaje natural, y el resultado es una tabla
> lista para leer o pasar al Report Builder.
> Inmediato, accionable, sin intermediarios."

---

### S10 — Manuals Chat: flujo RAG `(~0:40)`

> "Para la consulta de manuales el flujo es diferente.
>
> La pregunta del usuario llega a un webhook de n8n,
> que realiza el retrieval contextual sobre los documentos indexados,
> y envia el contexto recuperado al LLM para que genere la respuesta.
>
> El resultado es una respuesta precisa, con el fragmento relevante del manual,
> en vez de un PDF de quinientas paginas que el operario tiene que buscar a mano."

---

### S11 — Workflow n8n `(~0:30)`

> "Este es el workflow de n8n que orquesta el pipeline RAG.
> Podeis ver como se gestiona la recepcion del mensaje, el retrieval,
> el ensamblado del contexto y el envio al LLM.
> n8n nos da flexibilidad para modificar el pipeline sin tocar el codigo de la app."

---

### S12 — Resultado: Manuals Chat `(~0:30)`

> "Y aqui el resultado: el operario pregunta algo sobre el software del centro de control
> y recibe una respuesta contextualizada, con el fragmento de documentacion relevante.
> Soporte tecnico rapido sin salir de la plataforma."

---

### S13 — Report Builder: flujo `(~0:45)`

> "El tercer flujo es el Report Builder.
>
> El usuario selecciona los datos que quiere visualizar.
> La IA analiza el tipo de dato y recomienda la visualizacion mas adecuada:
> barras, lineas, tabla, lo que mejor represente la informacion.
> Se generan las graficas con Plotly, el usuario puede ajustarlas
> y finalmente exporta el reporte completo en PDF o CSV."

---

### S14-S17 — Ejemplos de reportes `(~1:10 total)`

> **S14** – "Primer ejemplo de reporte generado: orientado a lectura rapida con resumen ejecutivo."

> **S15** – "Segundo ejemplo con una distribucion visual diferente, mas analitica."

> **S16** – "Tercero, con formato comparativo entre periodos o lineas."

> **S17** – "Y el cuarto, con exportacion lista para compartir o incluir en un informe."

*(10-18 segundos por cada uno, solo senalar el reporte y pasar)*

---

### S19 — Validacion funcional y experiencia de uso `(~1:00)`

> "En terminos de validacion, los tres flujos principales han sido probados
> de forma completa: el chat de datos con generacion SQL segura,
> el Report Builder con exportacion real a PDF y CSV,
> y el Manuals Chat con recuperacion contextual via RAG.
>
> En experiencia de uso, el valor principal es este:
> cualquier operario, sin conocimiento tecnico, puede hacer una consulta,
> obtener una respuesta y exportar un reporte en menos de un minuto.
> Sin esperar a un especialista, sin escribir SQL, sin abrir un PDF de manuales.
>
> Ademas, todo pasa por autenticacion corporativa con Azure EntraID,
> lo que garantiza gobernanza y trazabilidad desde el primer dia."

---

### S21 — Summary `(~0:45)`

> "El resumen es directo.
>
> Que resuelve: acceso a datos operativos en tiempo real para perfiles no tecnicos,
> sin dependencia de especialistas.
>
> Como lo hace: combinando agentes IA, validacion SQL, RAG con n8n
> y exportacion de resultados en formatos reutilizables.
>
> Que valor aporta: reduce la friccion operativa, acelera decisiones en tiempo real
> y aporta trazabilidad tecnica con gobierno corporativo integrado.
>
> La base esta lista para escalar de PoC a entorno productivo."

---

### S22 — Posibles preguntas tecnicas `(~0:50)`

> "Antes de pasar a preguntas, anticipo las dos que suelen surgir.
>
> Primera: como se garantiza que el SQL sea seguro.
> La respuesta es: cadena de seguridad en tres pasos.
> Guardrails en el prompt, validacion previa del SQL generado con sqlglot,
> y ejecucion en modo solo lectura contra la base de datos, sin permisos de escritura.
> El LLM nunca puede modificar datos.
>
> Segunda: cual fue mi rol.
> Este proyecto parte de una PoC existente.
> Mi contribucion fue mejorar la experiencia y la capa IA:
> ajuste y refinado de prompts, correccion de errores funcionales,
> y generacion de datos sinteticos con el mismo schema de la base de datos real
> para poder hacer testing en desarrollo sin necesidad de datos de produccion."

---

### S23 — Cierre `(~0:25)`

> "Gracias por vuestra atencion.
> Quedo disponible para cualquier pregunta o comentario."

---

## Respuestas rapidas para Q&A

**"Que pasa si el LLM genera SQL incorrecto o peligroso?"**
> "Tenemos tres capas: guardrails en el prompt que restringen el output a SELECT,
> validacion con sqlglot antes de ejecutar, y permisos de solo lectura en la base de datos.
> Cualquier intento de escritura falla antes de llegar a la BBDD."

**"Cual fue exactamente tu rol en este proyecto?"**
> "Parti de una aplicacion base y me centre en la capa IA y UX:
> refinado de prompts, correccion de bugs funcionales
> y generacion de datos sinteticos realistas para testing en desarrollo
> usando el mismo schema de la base de datos de produccion."

**"Por que Streamlit y no un frontend mas robusto?"**
> "Para una PoC, Streamlit nos permite iterar muy rapido con Python puro.
> La arquitectura por capas esta pensada para que el frontend se pueda
> reemplazar sin tocar la logica de IA ni los datos."

**"Como funciona la autenticacion?"**
> "Azure EntraID con Graph API: los usuarios se autentican con sus credenciales corporativas
> y los permisos se gestionan a nivel de tenant, no en la aplicacion."
