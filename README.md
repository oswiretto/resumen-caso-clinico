# Resumen de caso clínico — Skill de IA para médicos

### Una herramienta práctica para organizar información clínica con inteligencia artificial

![Antes y después: caso ficticio](IA%20en%20la%20consulta%20m%C3%A9dica_%20antes%20y%20despu%C3%A9s.png)

**Autor:** Oswaldo Retto — Médico especialista en Aparato Digestivo.

## ¿Qué es?

Una habilidad (*skill*) desarrollada para Claude AI y ChatGPT que permite transformar información clínica no estructurada en un resumen organizado, claro y fácil de incorporar a la historia clínica electrónica.

Surge de una necesidad cotidiana: facilitar la revisión de historias clínicas, especialmente en visitas sucesivas, donde es necesario integrar información de diferentes fechas y exploraciones.

**No requiere conocimientos de programación para utilizarla.**

## ¿Qué hace?

- Identifica el diagnóstico inicial y el motivo de la visita.
- Organiza antecedentes, tratamientos y evolución clínica.
- Genera tablas comparativas de analíticas con diferentes fechas y señala los valores alterados.
- Resume endoscopias, anatomía patológica y otras exploraciones.
- Incluye un comentario clínico orientativo basado en guías y consensos.
- Señala información relevante que falta para completar la valoración.
- Admite textos en castellano y catalán.
- Genera texto plano para facilitar su incorporación a la historia clínica electrónica.

Está diseñada principalmente para Gastroenterología, aunque su estructura puede adaptarse a otras especialidades.

## ¿Cómo utilizarla?

1. Descargar el archivo `SKILL.md` del repositorio.
2. En Claude: Ajustes, apartado de skills, subir el archivo. En ChatGPT: adjuntar `SKILL.md` en un chat nuevo y pedir que cree la Habilidad sin cambiar nada.
3. Introducir un caso clínico ficticio o información clínica adecuadamente anonimizada, respetando las políticas de protección de datos del centro.
4. Revisar el resumen generado antes de utilizarlo.

La estructura del resultado puede adaptarse a las necesidades de cada profesional.

## Pruebas realizadas

La herramienta se ha evaluado inicialmente con **10 casos clínicos ficticios**, incluyendo situaciones habituales, casos complejos y ejemplos con errores deliberados.

Las pruebas examinan la organización de información, las conversiones de unidades, el formato de las analíticas, la detección de datos identificativos y el comportamiento ante información insuficiente.

Resultado: 10 de 10 casos con el comportamiento esperado; dos detalles menores de formato.

Los casos y el informe están documentados en `casos-de-prueba.md`.

**Estas pruebas no constituyen una validación clínica formal.**

## Seguridad y limitaciones

Esta herramienta es un **prototipo educativo de apoyo a la organización de información clínica**.

- No es un producto sanitario validado.
- No sustituye el juicio clínico ni la responsabilidad del médico.
- Los resultados, las cifras y las recomendaciones deben revisarse.
- Las referencias a guías clínicas pueden contener errores o quedar desactualizadas.
- Debe utilizarse únicamente con información adecuadamente anonimizada y conforme a la normativa y las políticas institucionales aplicables.
- La eliminación de identificadores directos no garantiza por sí sola una anonimización completa.

No debe utilizarse como sistema autónomo de diagnóstico o decisión terapéutica.

## Origen del proyecto

Este proyecto se ha desarrollado durante mi formación en inteligencia artificial aplicada a la medicina con **Learn Health AI, de Joaquín Fernández Sande**.

Su objetivo es mostrar que los médicos asistenciales, incluso sin conocimientos de programación, podemos utilizar herramientas de IA para abordar necesidades concretas de nuestra práctica diaria.

**La innovación no siempre requiere desarrollar sistemas complejos. A veces empieza por organizar mejor la información que ya tenemos.**

## Licencia

Este proyecto se distribuye bajo licencia [Creative Commons Atribución 4.0 Internacional (CC BY 4.0)](LICENSE). Puede usarse y adaptarse libremente citando al autor.
