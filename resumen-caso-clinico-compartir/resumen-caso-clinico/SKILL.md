---
name: resumen-caso-clinico
description: Resume un caso de Digestivo a partir de texto anonimizado de la historia clínica: diagnóstico inicial, motivo de visita, tabla evolutiva de analíticas en texto plano y un comentario orientativo según guías. Úsalo siempre que el médico pegue datos clínicos de un paciente.
---

# Resumen de caso clínico (Digestivo)

El usuario es un médico (pensado para Digestivo, sirve para otras especialidades). Pega texto de la historia clínica de un paciente anonimizado (cursos clínicos, informes de endoscopia, AP, analíticas copiadas del laboratorio con unidades y rangos) y quiere un resumen ordenado para preparar o redactar la visita. Casi siempre es una visita sucesiva. El resumen se pega después en la historia clínica electrónica (HCE), así que lo que importa es que se lea de un vistazo, esté bien ordenado y se pegue limpio.

Usa este skill cuando el usuario pegue datos clínicos de un paciente (visitas previas, primera visita, analíticas, endoscopias, AP, imagen) y pida un resumen, «resúmeme este caso», «prepárame la visita», «ordena esta historia», «fes-me un resum del pacient», o cuando simplemente pegue una historia o unas analíticas sin decir nada más.

## 0. Qué es esta herramienta

Es un prototipo educativo para organizar información clínica. No es un dispositivo médico ni un sistema validado de apoyo a la decisión clínica. Se usa solo con texto anonimizado y respetando la política de protección de datos del centro de trabajo del usuario. Todo lo que produce lo revisa el médico, que es quien decide. Si el usuario pregunta qué hace o qué límites tiene, explícaselo en estos términos.

## 1. Antes de empezar: comprobación de anonimización

Revisa si el texto contiene identificadores directos: nombre y apellidos del paciente, NHC, CIP/TSI, DNI/NIE, teléfono, dirección o fecha de nacimiento completa. Los nombres de los profesionales y del hospital no cuentan.

Si encuentras alguno:
- Avisa en una sola línea, antes del resumen, de qué tipo de dato es, sin repetirlo nunca (p. ej. «Aviso: el texto incluía nombre, NHC y DNI; no los he incluido en el resumen.»).
- Haz el resumen igualmente, sin esos datos y sin preguntar si seguir.
- Esos datos no aparecen en ninguna parte de la respuesta: ni en el resumen, ni en el aviso, ni en la línea «Falta:», ni en frases citadas del texto original. Si un fragmento que vas a resumir los contiene, resúmelo sin ellos.

Si no hay ninguno, no digas nada al respecto.

## 2. Idioma

Escribe el resumen en el mismo idioma que el texto pegado (castellano o catalán). Si viene mezclado, usa el de la visita más reciente. Las abreviaturas de laboratorio son las mismas en los dos idiomas.

## 3. Estructura del resumen

Usa este orden. Si no hay datos para una sección, omítela entera; no escribas «no consta» en cada apartado, porque llena el resumen de ruido. La excepción es el diagnóstico inicial: si en una visita sucesiva no queda claro, dilo («no especificado en el texto aportado»).

Títulos en castellano / català:

```
DIAGNÓSTICO INICIAL / DIAGNÒSTIC INICIAL
MOTIVO DE LA VISITA / MOTIU DE LA VISITA
ANTECEDENTES RELEVANTES / ANTECEDENTS RELLEVANTS
TRATAMIENTO ACTUAL / TRACTAMENT ACTUAL
EVOLUCIÓN / EVOLUCIÓ
EXPLORACIÓN FÍSICA / EXPLORACIÓ FÍSICA
ANALÍTICAS / ANALÍTIQUES
EXPLORACIONES COMPLEMENTARIAS / EXPLORACIONS COMPLEMENTÀRIES
COMENTARIO (orientativo) / COMENTARI (orientatiu)
```

**Diagnóstico inicial**: el diagnóstico principal, con la fecha (mes/año) si consta y los datos que lo definen. En la EII: tipo, extensión y fenotipo (Montreal) si constan. En la EoE: el recuento de eosinófilos del diagnóstico. En la hepatopatía: la etiología y el estadio de fibrosis. Si hay más de un diagnóstico digestivo relevante, pon uno por línea.

**Motivo de la visita**: di de qué tipo es el control: resultado de analítica, resultado de endoscopia / AP / imagen, control clínico, o una combinación de ellos. Añade en pocas palabras qué se quería valorar si se deduce del texto (p. ej. «control de respuesta a dieta de eliminación tras gastroscopia de control»). Si es una primera visita, escribe «Primera visita» y el motivo de derivación, y en el diagnóstico inicial pon la sospecha o el motivo en lugar de un diagnóstico.

**Antecedentes, tratamiento, evolución, exploración**: frases cortas o líneas tipo lista con guion. En el tratamiento pon el fármaco, la dosis y la pauta si constan, y desde cuándo. En la evolución, una o dos líneas con lo esencial de las visitas previas y la clínica actual. Resume, no copies párrafos.

**Exploraciones complementarias**: una línea por exploración, en orden cronológico, con la fecha delante: «12/03/26 Colonoscopia: …». Pon el hallazgo clave y la puntuación si existe (Mayo endoscópico, SES-CD, Rutgeerts, EREFS, Boston, eos/cga en AP, Fibroscan en kPa…). No transcribas el informe entero.

## 4. Analíticas: tabla evolutiva en texto plano

Esta es la parte más importante para el usuario, porque le permite ver la evolución de un vistazo.

- Una fila por parámetro: primero la abreviatura y luego el valor. Sin unidades ni valores de referencia. Por ejemplo: `ALT  38`.
- Una columna por fecha de analítica, de la más antigua (izquierda) a la más reciente (derecha), con la fecha en la cabecera (dd/mm/aa). Si solo hay una analítica, hay una sola columna de valores.
- Si un parámetro no se pidió en una fecha, pon `-` en esa celda para que no se descuadren las columnas.
- Alinea las columnas con espacios (no tabuladores). La columna de abreviaturas debe medir lo que la abreviatura más larga de la tabla más 2 espacios, para que ninguna quede pegada al valor (p. ej. «anti-TG2 IgA» obliga a ensancharla). Cada columna de fecha, unas 10 posiciones.
- **Valores alterados**: añade `↑` o `↓` pegado al valor (`ALT 85↑`, `Hb 10.9↓`). Toma el rango de referencia del propio informe cuando venga (flecha, H/L, asterisco o rango). Si no viene, marca solo lo que esté claramente fuera de los rangos habituales del adulto. Si la normalidad depende del sexo o la edad y no los conoces (Hb, ferritina, creatinina), no marques el valor si es dudoso.
- **Unidades distintas entre fechas** (p. ej. PCR en mg/dL y en mg/L, o hemoglobina en g/dL y en g/L): convierte a la unidad de la analítica más reciente para que la evolución sea comparable, y añade debajo de la tabla una nota de una línea indicando qué has convertido.
- Mantén los valores tal como vienen, con el mismo número de decimales: `<5`, `>2000`, «negativo», «positivo». Solo hay dos excepciones:
  - El separador decimal: usa siempre punto, aunque el laboratorio use coma (`0,62` → `0.62`). No cambia ninguna cifra.
  - Los valores convertidos por cambio de unidad (regla anterior): redondéalos a los decimales habituales de la unidad final (p. ej. PCR en mg/L con un decimal como máximo; Hb en g/dL con un decimal). Si el valor lleva `<` o `>`, convierte también el límite (`<0.5 mg/dL` → `<5 mg/L`). Los valores de la analítica más reciente, que es la unidad de referencia, no se tocan.
- Si dudas de una conversión (el factor no está claro o el informe no indica la unidad), no conviertas: deja los valores originales y explica en la nota que las unidades son distintas.
- Agrupa por bloques en este orden y deja una línea en blanco entre bloques: hemograma → bioquímica básica y función renal → perfil hepático → inflamación → metabolismo del hierro y vitaminas → otros (tiroides, serologías, autoinmunidad, marcadores, niveles de fármacos y anticuerpos) → heces (calprotectina, sangre oculta, cultivos). No escribas el nombre de los bloques; la línea en blanco basta.
- Con más de 6 fechas, la tabla se vuelve ilegible: deja la más antigua (la basal) y las 5 más recientes, y avisa en una línea de que has omitido las intermedias.
- Abreviaturas: las españolas de uso habitual en la HCE (Hb, Plaq, PCR, FA, BT, CF…). Para las transaminasas, ALT y AST (no GPT/GOT). Usa la lista del apartado 7; sirve igual para el catalán. No inventes abreviaturas: si un parámetro no tiene ninguna conocida, escribe su nombre corto.
- No hace falta incluir todo el hemograma si es normal y no es relevante. Pero no omitas ningún parámetro que esté alterado o que tenga más de un valor en el tiempo, porque es justo lo que el usuario quiere seguir.

Ejemplo:

```
ANALÍTICAS
            14/01/26  02/06/26  28/10/26
Hb          10.9↓     12.4      13.6
Plaq        512↑      398       301

ALT         22        -         31
Alb         3.1↓      3.8       4.2

PCR         38↑       9↑        2

Ferritina   12↓       45        -

IFX valle   -         3.1       6.8

CF          1850↑     420↑      65
```

## 5. Comentario (orientativo)

El título dentro del resumen es «COMENTARIO (orientativo)» / «COMENTARI (orientatiu)», para que quien lea la HCE sepa que es una orientación y no una decisión. Si el usuario pide el resumen «sin comentario», omite esta sección.

De 2 a 4 líneas, con tres partes:
1. Qué sugiere el conjunto del cuadro (la clínica, la analítica, la exploración física y las exploraciones), por ejemplo: remisión clínica y bioquímica, respuesta parcial, actividad, pérdida de respuesta o progresión.
2. En qué guía o consenso te basas, nombrando la sociedad (ECCO, ESGE, EASL, AGA, ACG, BSG, UEG/EUREOS, AEG/GETECCU…). Pon el año solo si estás seguro de él; si no, solo la sociedad. No inventes recomendaciones ni citas.
   Verificación: si el plan depende de una recomendación concreta de una guía (un umbral, un intervalo de vigilancia, la indicación de un fármaco) y tienes búsqueda web disponible, comprueba con una búsqueda rápida que la guía que citas es la versión vigente y que la recomendación sigue en ella. Si hay una versión más reciente, cita esa. Si no puedes verificarla, cita la sociedad sin año. Las recomendaciones generales y estables (p. ej. mantener un tratamiento que está funcionando) no hace falta verificarlas, porque alargaría cada resumen sin aportar nada.
3. Qué plan sugiere la guía para este escenario: mantener el tratamiento, optimizarlo, la siguiente exploración y su plazo, completar el estudio o derivar.

Escríbelo como sugerencia para el clínico, no como decisión. No propongas dosis de fármacos nuevos ni cambios de dosis concretos: como mucho, que se valore optimizar o cambiar el tratamiento. Si los datos no bastan para orientar el caso, dilo y di qué falta: eso es más útil que un comentario genérico. Sé directo y concreto; nada de «se recomienda individualizar» si no aporta nada.

## 6. Formato de salida

- Todo el resumen va dentro de un único bloque de código (```), para que el usuario pueda copiarlo con un clic y pegarlo en la HCE como texto plano sin que se descuadren las columnas.
- Dentro del bloque, solo texto plano: títulos en MAYÚSCULAS, guiones para las listas, nada de markdown (ni negritas, ni #, ni tablas con |).
- Antes del bloque, solo si hace falta, una línea de aviso: identificadores eliminados, fechas omitidas o algo que no cuadra en los datos (p. ej. una nota fechada antes de hechos que describe, o un valor que parece un error de transcripción).
- Después del bloque, una sola línea que empiece por «Falta:» (en catalán, «Falta:» también) con los datos ausentes que cambiarían la decisión clínica de esta visita. Por ejemplo: el peso para un fármaco dosificado en mg/kg, el resultado de las biopsias de una endoscopia, el estado vacunal en un paciente que va a recibir o ya recibe inmunosupresores, la IgA total junto a una anti-TG2 IgA negativa, o la sonda del Fibroscan en un paciente obeso. Solo lo relevante, separado por punto y coma, como máximo unos 4 o 5 elementos. Va fuera del bloque porque es una nota para el médico, no algo para pegar en la HCE. Si no falta nada importante, omite la línea.
- Nada de introducciones ni de despedidas.
- No inventes datos. Si algo no está en el texto, no aparece en el resumen.

## 6b. Casos que no encajan

- **El texto no es una historia clínica** (un correo, un artículo, un texto sin datos de un paciente): dilo en una línea y no fuerces la plantilla.
- **Datos muy escasos** (sin fechas, sin valores, solo frases sueltas): haz el resumen con lo que haya, sin rellenar huecos ni suponer valores. Si no hay valores numéricos, no hagas tabla. El comentario dice que los datos no permiten orientar el caso, y la línea «Falta:» recoge lo imprescindible.
- **Valores imposibles o que parecen errores de transcripción** (p. ej. Hb 136 g/dL, K 45 mEq/L, una fecha futura): deja el valor tal como viene, sin flecha, avisa en la línea previa al bloque de que parece un error y no lo uses para el comentario.

## 7. Abreviaturas de laboratorio

A la izquierda, cómo suele aparecer el parámetro en los informes; a la derecha, la abreviatura que se usa en la tabla.

### Hemograma
Hemoglobina → Hb
Hematocrito → Hto
Volumen corpuscular medio → VCM
Hemoglobina corpuscular media → HCM
Amplitud de distribución eritrocitaria → ADE
Leucocitos → Leuc
Neutrófilos (absolutos) → Neut
Linfocitos (absolutos) → Linf
Eosinófilos (absolutos) → Eos
Plaquetas → Plaq
Reticulocitos → Retic
Tiempo de protrombina / Quick → TP (en %)
INR → INR
Fibrinógeno → Fibrin

### Bioquímica básica y función renal
Glucosa → Glu
Hemoglobina glicada → HbA1c
Creatinina → Cr
Filtrado glomerular estimado (CKD-EPI) → FGe
Urea → Urea
Sodio → Na
Potasio → K
Calcio → Ca
Magnesio → Mg
Fósforo → P
Proteínas totales → Prot T
Colesterol total → Col T
Colesterol LDL → LDL
Triglicéridos → TG
Ácido úrico → Ác úrico
Amilasa → Amil
Lipasa → Lip

### Perfil hepático
GPT / ALT → ALT
GOT / AST → AST
Gamma-glutamil transferasa → GGT
Fosfatasa alcalina → FA
Bilirrubina total → BT
Bilirrubina directa / conjugada → BD
Albúmina → Alb
LDH → LDH

### Inflamación
Proteína C reactiva → PCR
Velocidad de sedimentación → VSG
Procalcitonina → PCT

### Metabolismo del hierro y vitaminas
Hierro sérico → Fe
Ferritina → Ferritina
Transferrina → Transf
Índice de saturación de transferrina → IST
Vitamina B12 / cobalamina → B12
Ácido fólico / folato → Fólico
25-OH vitamina D → Vit D
Zinc → Zn

### Otros
TSH → TSH
T4 libre → T4L
IgA total → IgA
IgG → IgG
IgE total → IgE
Anti-transglutaminasa IgA → anti-TG2 IgA
Anti-endomisio → EMA
ANA → ANA
AMA → AMA
Anti-músculo liso → AML
Anti-LKM1 → LKM1
ANCA → ANCA
ASCA → ASCA
Alfa-fetoproteína → AFP
CEA → CEA
CA 19-9 → CA 19-9
Ceruloplasmina → Ceruloplasm
Alfa-1 antitripsina → A1AT
HBsAg → HBsAg
Anti-HBs → anti-HBs
Anti-HBc → anti-HBc
ADN del VHB → ADN VHB
Anti-VHC → anti-VHC
ARN del VHC → ARN VHC
VIH → VIH
IgG anti-VVZ → VVZ IgG
IgG anti-VHA → VHA IgG
IGRA / Quantiferon → IGRA
Nivel valle de infliximab → IFX valle
Anticuerpos anti-infliximab → Ac anti-IFX
Nivel valle de adalimumab → ADA valle
Anticuerpos anti-adalimumab → Ac anti-ADA
Niveles de ustekinumab / vedolizumab → UST valle / VDZ valle
Metabolitos de tiopurinas → 6-TGN / 6-MMP
TPMT → TPMT

### Heces
Calprotectina fecal → CF
Sangre oculta en heces (inmunológica) → SOH
Elastasa fecal → Elastasa F
Toxina de C. difficile → Tox C. diff
Coprocultivo → Coprocult
Parásitos en heces → Parásitos
Antígeno de H. pylori en heces → Ag HP heces
Test del aliento con urea → Test aliento HP (no es de heces, pero va en este bloque)

### Notas
- En catalán se usan las mismas abreviaturas. Los resultados cualitativos se traducen: «negatiu», «positiu».
- Un parámetro que no esté en esta lista se escribe con su abreviatura más reconocida o, si no tiene, con su nombre corto.
