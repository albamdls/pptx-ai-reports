# Guion breve de presentacion (10-13 min)

## Objetivo de tiempo
- Duracion objetivo: 11:30 min
- Rango valido: entre 10:00 y 13:00
- Regla practica: si vas por 6:00 al terminar la seccion 7, vas bien.

## Estrategia de ritmo
- Habla en bloques de 20-40 segundos por slide.
- En slides con imagen, describe solo 1 idea clave y pasa a la siguiente.
- Evita leer texto literal: resume en una frase + valor para operaciones.

## Guion por diapositiva

### S1 Portada (0:40)
"Soy Alba Mora de la Sen, de Siemens Mobility. Presento una PoC de analitica operativa asistida por IA para consultar datos en lenguaje natural y generar reportes tecnicos de forma rapida."

### S2 Indice (0:30)
"Voy a ir de problema a solucion: capacidades, tecnologia, arquitectura, validacion y cierre con preguntas tecnicas."

### S3 Problema, objetivo y alcance (1:00)
"El problema es claro: hay datos operativos en tiempo real, pero no todos los perfiles pueden consultarlos con SQL. El objetivo es permitir consultas, reportes y soporte documental sin depender de un especialista."

### S4 Capacidades funcionales (0:55)
"La solucion se apoya en cuatro capacidades: chat SQL seguro, narrativa de datos, constructor de reportes y chat de manuales con RAG."

### S5 Interfaz visual (0:35)
"Esta es la interfaz principal: un flujo unico donde el usuario pregunta, recibe resultados y puede pasar a reporte."

### S6 Tecnologias usadas (0:55)
"Tecnologicamente, combinamos Streamlit en frontend, stack de IA para razonamiento y SQL, e integraciones corporativas para autenticacion y despliegue."

### S7 Arquitectura por capas (0:55)
"Mantengo esta slide porque explica robustez tecnica: separacion por capas para evolucionar la PoC sin romper la operacion. Interfaz, aplicacion, IA, datos e infraestructura estan desacopladas."

### S8 Chat de datos - flujo (0:45)
"Aqui se ve el flujo: pregunta en lenguaje natural, generacion SQL con control, ejecucion segura y respuesta en tabla mas narrativa."

### S9 Resultado tabla (0:30)
"Ejemplo real de salida tabular: respuesta inmediata y accionable para operacion."

### S10 Manuals Chat - flujo RAG (0:40)
"Para manuales tecnicos usamos RAG: recuperacion contextual y respuesta precisa para soporte rapido."

### S11 Workflow n8n (0:30)
"Este workflow muestra como orquestamos el pipeline de retrieval y generacion de forma flexible."

### S12 Resultado Manuals Chat (0:30)
"Aqui se ve la respuesta final del asistente sobre documentacion, con contexto util para el operario."

### S13 Report Builder - flujo (0:45)
"Desde datos validados pasamos a visualizacion y exportables. La IA ayuda a escoger la mejor grafica segun el tipo de dato."

### S14-S17 Ejemplos de reportes (1:10 total)
- S14 (0:18): "Ejemplo de reporte orientado a lectura rapida."
- S15 (0:18): "Segundo ejemplo con otra distribucion visual."
- S16 (0:17): "Tercer ejemplo para analisis comparativo."
- S17 (0:17): "Cuarto ejemplo con formato listo para compartir."

### S19 Validacion funcional y experiencia de uso (1:00)
"Se valida el flujo completo: consulta segura, narrativa, reportes y manuals chat. En experiencia de uso, el valor principal es reducir dependencia tecnica y acelerar decisiones operativas."

### S21 Summary (0:45)
"En resumen: resolvemos acceso a datos en tiempo real para perfiles no tecnicos, con trazabilidad y base clara para escalar la PoC."

### S22 Posibles preguntas tecnicas (0:50)
"Si surge esta parte, las dos respuestas clave son: seguridad SQL con guardrails y validacion en solo lectura; y mi rol centrado en mejoras de diseno, prompts, correcciones y datos sinteticos para testing."

### S23 Cierre (0:25)
"Gracias por vuestra atencion. Quedo disponible para preguntas."

## Control de tiempo en vivo (con cronometro)
- Checkpoint 1 (min 3:00): deberias estar entre S6 y S7.
- Checkpoint 2 (min 6:00): deberias estar entre S11 y S13.
- Checkpoint 3 (min 9:00): deberias estar entre S19 y S21.
- Si vas lento: recorta S14-S17 a 10 segundos cada una.
- Si vas rapido: amplia S7 y S19 con una frase extra de valor tecnico.

## Mini respuestas preparadas (Q&A)
- "Que garantiza la seguridad en SQL?" -> "Prompting con guardrails, validacion previa y ejecucion en modo solo lectura sin permisos de escritura."
- "Cual fue mi rol?" -> "Parti de una PoC existente y me enfoque en mejoras de UX e IA: prompts, correcciones y datos sinteticos realistas para pruebas."
