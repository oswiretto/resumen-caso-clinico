# resumen-caso-clinico

Skill para Claude y ChatGPT que convierte el texto de una historia clínica anonimizada (visitas previas, analíticas, endoscopias, anatomía patológica, imagen) en un resumen ordenado para preparar una visita sucesiva de Digestivo, listo para pegar en la historia clínica electrónica.

Autor: Oswaldo Retto, gastroenterólogo. Construido como alumno de Learn Health AI.

## Aviso

Prototipo educativo, no validado. No es un dispositivo médico ni un sistema de apoyo a la decisión clínica.

- Úsalo solo con texto anonimizado y conforme a la política de protección de datos de tu centro. Quitar el nombre, el NHC o el DNI no siempre basta para que un caso no se pueda identificar.
- El comentario final es orientativo. El médico revisa todo el resumen y decide.
- Las guías clínicas cambian: comprueba la recomendación antes de aplicarla.

## Qué produce

- Diagnóstico inicial y motivo de la visita.
- Antecedentes, tratamiento actual, evolución y exploración, en frases cortas.
- Tabla evolutiva de analíticas en texto plano: abreviatura y valor, sin unidades ni rangos, una columna por fecha, con ↑ ↓ en los valores alterados y conversión de unidades cuando cambian entre fechas.
- Exploraciones complementarias con la fecha y su puntuación (SES-CD, Mayo, EREFS, Fibroscan…).
- Comentario orientativo de 2 a 4 líneas: qué sugiere el cuadro, en qué guía se basa y qué plan propone.
- Una línea «Falta:», fuera del resumen, con los datos que cambiarían la decisión de esa visita.

Responde en el idioma del texto pegado (castellano o catalán). Si el texto contiene identificadores, avisa en una línea y los excluye del resumen.

## Cómo instalarlo

- Claude: en Ajustes, apartado de skills, sube el archivo .zip.
- ChatGPT: en un chat nuevo, adjunta SKILL.md y pide «Crea la Habilidad con exactamente el contenido de este archivo, sin cambiar nada». Comprueba que el texto no se ha recortado antes de instalarla.

## Cómo usarlo

Pega la historia clínica anonimizada y escribe, por ejemplo, «resúmeme este caso». Si no se activa solo, menciona el skill por su nombre. Para obtener el resumen sin el comentario, pide «sin comentario».

## Pruebas

Probado con 10 casos ficticios: 5 habituales, 3 inusuales y 2 que deberían fallar de forma controlada. Los casos y los resultados están en casos-de-prueba.md, y los textos de entrada en la carpeta evals/.
