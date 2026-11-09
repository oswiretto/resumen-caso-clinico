# Casos de prueba: resumen-caso-clinico

Diez casos ficticios, construidos para probar el skill. Ninguno corresponde a un paciente real. El texto de entrada de cada caso está en evals/<nombre-del-caso>/prompt.md.

Probado el 09/11/2026 con Claude (versión para compartir del skill). Resultado: 10 de 10 se comportan como se esperaba.

## Casos habituales (5)

1. crohn-infliximab-evolutivo
   Qué prueba: Crohn ileal con tres analíticas, una de ellas con la PCR en mg/dL y otra en mg/L, y colonoscopia de control.
   Resultado esperado: tabla con tres fechas, PCR convertida a la misma unidad y con una nota que lo indica, flechas en los valores alterados, comentario de remisión con ECCO y plan.
   Resultado: correcto (PCR 42↑ 11↑ 2, nota de conversión, línea «Falta:» con el peso, el estado vacunal y las biopsias).

2. eoe-ibp-catalan
   Qué prueba: texto en catalán, una sola analítica y dos gastroscopias.
   Resultado esperado: resumen en catalán, una columna de analítica, EREFS y eos/cga de las dos exploraciones, y una guía citada.
   Resultado: correcto.

3. hipertransaminasemia-resultados
   Qué prueba: estudio de hepatopatía con dos analíticas, ecografía y Fibroscan.
   Resultado esperado: «-» en los parámetros que solo constan en la segunda analítica, MASLD con fibrosis en zona gris y referencia a EASL.
   Resultado: correcto (calcula el FIB-4 y en la línea «Falta:» pide la sonda del Fibroscan y la IgA total).

4. primera-visita-anemia
   Qué prueba: primera visita por anemia ferropénica en un varón de 63 años que toma AAS.
   Resultado esperado: «Primera visita» y la sospecha en el diagnóstico inicial, y estudio endoscópico bidireccional según la BSG.
   Resultado: correcto (cita la guía BSG de anemia ferropénica de 2021 y el documento BSG/ACPGBI sobre FIT de 2025).

5. vigilancia-polipos-sin-analitica
   Qué prueba: resultado de AP tras polipectomía, sin ninguna analítica.
   Resultado esperado: sin sección de analíticas e intervalo de vigilancia según la ESGE.
   Resultado: correcto (adenoma de 12 mm, colonoscopia a los 3 años según la ESGE de 2020).

## Casos inusuales (3)

6. cu-muchas-fechas
   Qué prueba: colitis ulcerosa con 10 fechas de calprotectina y PCR.
   Resultado esperado: tabla con la fecha basal y las 5 más recientes, y un aviso de las fechas omitidas.
   Resultado: correcto (además, responde a la pregunta de la paciente sobre la mesalazina rectal).

7. cirrosis-unidades
   Qué prueba: dos laboratorios con unidades distintas (Hb en g/L, bilirrubina y creatinina en µmol/L, albúmina en g/L).
   Resultado esperado: valores convertidos a las unidades de la analítica más reciente, con nota, y un plan de cribado del CHC.
   Resultado: correcto. Al comprobar si la guía estaba vigente, encontró y citó Baveno VIII (2026) en lugar de Baveno VII. Detalle menor: escribe la creatinina convertida con dos decimales (0.90) y la otra con uno (0.9).

8. aviso-identificadores
   Qué prueba: un texto con nombre, NHC y DNI.
   Resultado esperado: un aviso sin repetir los datos y un resumen completo sin ellos.
   Resultado: correcto (ningún identificador en la respuesta; además, detecta que la nota está fechada antes de hechos que describe). Detalle menor: da los dos avisos en dos líneas, no en una.

## Casos que deben fallar de forma controlada (2)

9. datos-insuficientes
   Qué prueba: cuatro frases sin fechas ni valores.
   Resultado esperado: no inventa datos, no hace tabla, dice que los datos no permiten orientar el caso y recoge lo que falta.
   Resultado: correcto.

10. valor-imposible
    Qué prueba: una Hb de 136 g/dL, es decir, un error de transcripción.
    Resultado esperado: deja el valor tal cual, sin flecha, avisa de que parece un error y no lo usa para el comentario.
    Resultado: correcto («¿13.6 g/dL o 136 g/L?»).

## Limitaciones

- Diez casos ficticios no validan la herramienta para la práctica clínica. Solo comprueban que sigue las instrucciones.
- Las citas de las guías dependen del modelo y de que tenga búsqueda web. Hay que revisarlas siempre.
- No se ha probado con historias reales ni con formatos de laboratorio de otros centros.
