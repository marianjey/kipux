# KIPUX — Blueprint de diseño y especificación web
### Documento de trabajo para diseño, copy y desarrollo

**Preparado para:** Mariana — KIPUX (estudio contable digital, Tucumán)
**Fecha:** 31/08/2026
**Estado:** Borrador estratégico v1 — para revisión antes de pasar a diseñador/desarrollador

---

## Nota metodológica

Este documento se construyó a partir de dos fuentes:

1. **Material propio del proyecto** cargado en el workspace de KIPUX (tesis de negocio, modelo de dashboard, segmentación, pricing conceptual, roadmap).
2. **Investigación en vivo** de cinco jugadores reales del mercado argentino de contabilidad digital para monotributistas, hecha para este documento (no eran parte del material cargado, que solo contenía una lista de links sin analizar): **Contablix**, **Countax**, **Tributo Simple**, **Gestorando** y **Lannis**. El caso Lannis es especialmente relevante — es la plataforma de "contador IA" intimada por el Consejo Profesional de CABA en octubre 2025, y es un punto de contraste estratégico directo para KIPUX (ver sección 3).

No se cargaron capturas ni archivos de las webs de referencia mencionadas en el prompt original ("Lennis" y otras) — se investigaron en vivo en su lugar. Si tenés PDFs o capturas específicas que querías que analizara, decime y actualizo el documento.

**Regla que apliqué en todo el documento:** no inventé precios finales, matrícula profesional, razón social ni testimonios. Donde el documento necesita ese dato para quedar completo, está marcado como `[COMPLETAR: ...]`.

---

## 1. Resumen estratégico

KIPUX tiene una tesis sólida y poco común en este mercado: la mayoría de los competidores digitales argentinos eligen uno de dos caminos — **plataforma de autoservicio con contacto humano mínimo** (Tributo Simple, Gestorando) o **estudio tradicional con canal digital** (Contablix, Countax, vía WhatsApp y videollamada, sin dashboard). Ninguno de los cinco jugadores relevados combina **dashboard propio + respaldo profesional matriculado visible + anclaje geográfico local**. Esa combinación es el espacio libre que KIPUX puede ocupar.

Decisiones que tomo en este documento, con su fundamento:

| Decisión | Alternativas evaluadas | Elegida | Por qué |
|---|---|---|---|
| Tagline principal | "Tus números, claros" / "Contabilidad que se entiende" / "Automatizamos lo simple. Te acompañamos en lo importante." | **"Automatizamos lo simple. Te acompañamos en lo importante."** | Es la única que comunica el *modelo* (qué hace la máquina, qué hace el humano), no solo un beneficio genérico. Las otras dos podrían decirlas Contablix o Countax sin cambiar una palabra. |
| Mostrar precios en la web | Precio fijo público / todo a cotización / rango "desde" + calculadora | **Rango "desde" por plan + lógica de armado visible, sin cotizador obligatorio** | Contablix esconde el precio detrás de una llamada — eso contradice "transparencia", que es un diferencial que KIPUX reclama. Mostrar un piso concreto filtra mejor y genera confianza sin comprometer el margen en casos atípicos. |
| Tecnología para el MVP del sitio | WordPress / Webflow / Framer / Next.js | **Webflow** (con Framer como alternativa cercana) | Ver sección 21. |
| Cómo mostrar el dashboard en la web pública | Screenshot estático / mockup interactivo simulado / video | **Mockup interactivo simulado (HTML/CSS, sin datos reales) embebido en el hero y en su propia sección** | Es el elemento que más comunica "esto es una fintech, no un estudio de PDFs" — vale la inversión de producirlo bien. Ver sección 15. |
| Alcance geográfico en el copy | Solo "Tucumán" / solo "Argentina" / Tucumán como ancla + arquitectura escalable | **Tucumán como ancla explícita, con arquitectura de contenido y URLs que ya soportan expansión** | Pedido explícito del brief (regla 11). Se resuelve en el SEO (sección 20) y el sitemap (sección 5), no forzando "Tucumán" en cada página. |

**Lectura de las webs de referencia relevadas:** ninguna de las cinco arriesga a mostrar precio fijo y transparente combinado con un dashboard real. Contablix gana en prueba social (testimonios reales con foto) y en generación de leads (checklist descargable, calculadora, cotizador con IA). Tributo Simple y Gestorando ganan en producto (app real, freemium). Lannis gana en claridad de propuesta pero pierde en legitimidad profesional — ahí está la oportunidad más clara para KIPUX.

---

## 2. Análisis de las webs de referencia

| Elemento | Referencia | Qué funciona | Qué adoptar | Qué evitar |
|---|---|---|---|---|
| **Lead magnets y captura** | Contablix (checklist descargable, calculadora de cuota interactiva, cotizador con IA, Calendly embebido) | Múltiples puntos de entrada de baja fricción antes de pedir una decisión grande | La calculadora de cuota y un checklist ("¿estás en orden?") como imán de leads tempranos | El cotizador como único camino al precio — genera fricción y opacidad |
| **Prueba social** | Contablix (4 testimonios reales con foto de Google, rating 5.0) | Testimonios verificables, no genéricos | El formato (foto + nombre + rubro + cita corta), aplicado cuando existan clientes reales | Inventar testimonios antes de tenerlos — dejar el espacio preparado (ver sección 25 del brief / sección 6.6 más abajo) |
| **Onboarding sin fricción** | Contablix (reunión gratuita de 30 min, "no se firma nada ni se paga nada", autorización ARCA en <5 min) | Bajar la ansiedad inicial explicitando que no hay compromiso en el primer paso | El mensaje explícito de "no te comprometés en el paso 1" | El onboarding 100% dependiente de una llamada agendada — KIPUX debería poder arrancar sin hablar con nadie si el usuario quiere |
| **Producto / plataforma** | Tributo Simple (app + web, facturación, alertas, DDJJ, VEPs) y Gestorando (app, freemium) | Mostrar la plataforma como protagonista, no como anexo | La lógica de "la plataforma hace el trabajo repetitivo" comunicada con capturas/mockups reales, no con íconos genéricos | El tono "todo gratis" de Gestorando en el plan free — genera expectativa de que lo profesional también es gratis |
| **Pricing** | Gestorando (freemium: $0 / $13.000 trim. / alianzas) y Tributo Simple ($0 / $17.500/mes / a consultar) | Estructura escalonada de 3 niveles, con el nivel de entrada muy accesible | El escalonamiento en 3 niveles y el ancla de precio bajo de entrada | Un plan gratuito real — para KIPUX el gratis no aplica (hay trabajo profesional detrás desde el día uno); usar en cambio un plan de entrada con precio piso claro |
| **Contenido / SEO** | Countax (blog extenso: "Monotributo 2026", categorías por tema impositivo) | Volumen de contenido educativo indexable, actualizado por año fiscal | La lógica de un artículo "ancla" por año fiscal + categorías temáticas (ver sección 20) | El tono puramente informativo sin conexión a producto — cada artículo de Countax debería empujar a una acción y en general no lo hace con fuerza |
| **Posicionamiento / riesgo reputacional** | Lannis ("primer contador IA", USD 25/mes, intimado por el Consejo Profesional de CABA por presunto ejercicio ilegal de la profesión, Ley 20.488) | Propuesta de valor muy nítida y agresiva en precio para nómadas digitales | Nada de su posicionamiento — pero sí la lección: automatizar sin mostrar respaldo profesional matriculado es un riesgo legal y de confianza real en Argentina, no hipotético | Cualquier copy que sugiera que "la IA reemplaza al contador" o que difumine quién firma las declaraciones. KIPUX debe decir explícitamente "hay un contador matriculado detrás" — es diferencial *y* blindaje legal |
| **Estructura de home** | Tributo Simple (nav clara: Capacitación / Planes / Trámites / Organizaciones / Nosotros; hero con video; social proof con logos) | Navegación por intención de uso, no por organigrama interno | El video/demo corto en el hero como forma de mostrar producto sin texto | Menús con más de 5-6 ítems — ninguno de los relevados lo hace, y KIPUX tampoco debería |
| **Tono de marca** | Todos usan tono "cercano/emprendedor"; ninguno usa el registro técnico-tributario en el copy público | El registro coloquial argentino en el copy de cara al público | El tono, pero con una capa más de "producto tecnológico" que ninguno de los cinco logra del todo | Un tono infantilizado ("¡dale que va!") — el público de KIPUX incluye profesionales (abogados, arquitectos) que esperan seriedad con simplicidad, no informalidad excesiva |

**Conclusión de esta sección:** KIPUX no necesita inventar una categoría nueva de mensaje — necesita ejecutar mejor la combinación que nadie más está ejecutando: precio transparente + plataforma real + contador matriculado visible + anclaje local. Eso es lo que organiza todo el resto del documento.

---

## 3. Posicionamiento de KIPUX

### 3.1 Frase de posicionamiento (uso interno, no es copy de web)

> Para monotributistas, profesionales independientes y pequeños comercios de Tucumán que hoy dependen de WhatsApp y PDFs para saber si están al día, KIPUX es el estudio contable digital que muestra su situación fiscal en tiempo real y automatiza lo repetitivo — a diferencia de un estudio tradicional (todo manual, sin visibilidad) o de una app de autogestión tipo Gestorando/Tributo Simple (sin contador matriculado detrás con criterio profesional real), porque combina un dashboard propio con el respaldo de una contadora matriculada que revisa cada caso.

### 3.2 Mapa competitivo

```text
                    ALTA TRANSPARENCIA / PRODUCTO DIGITAL
                                    │
              Gestorando ●         │         ● KIPUX (posición buscada)
              Tributo Simple ●     │
                                    │
    SIN RESPALDO ───────────────────┼─────────────────── CON RESPALDO
    PROFESIONAL                     │                   PROFESIONAL VISIBLE
    VISIBLE                         │
                        ● Lannis    │    ● Contablix
                                    │    ● Countax
                                    │
                    BAJA TRANSPARENCIA / CANAL WHATSAPP+CALL
```

KIPUX es el único que puede ocupar el cuadrante superior derecho: plataforma real **y** contador matriculado visible. Ese cuadrante hoy está vacío en el mercado relevado.

### 3.3 Qué NO debe hacer KIPUX (ajuste a las hipótesis del material cargado)

El documento de proyecto original planteaba evitar "competir por precio" y "prometer todo incluido" — coincido con ambos puntos y agrego, a partir de la investigación de competencia:

- **No usar el término "IA" como promesa central.** El caso Lannis mostró que el mercado profesional argentino (Consejos Profesionales) reacciona duro contra cualquier mensaje que sugiera que la tecnología reemplaza el criterio del contador matriculado. KIPUX puede y debe automatizar, pero el copy tiene que decir "automatizamos tareas repetitivas" y no "contador IA" ni equivalentes.
- **No copiar el modelo "todo a cotización" de Contablix.** Contradice la transparencia que KIPUX reclama como diferencial.
- **No copiar el modelo "freemium" de Gestorando/Tributo Simple.** Un plan gratuito sugiere que no hay trabajo profesional real detrás, y erosiona el posicionamiento premium-accesible que busca KIPUX.

### 3.4 Mensajes de marca — evaluación de las 5 alternativas del material cargado

| Mensaje | Evaluación |
|---|---|
| "KIPUX — Tus números, claros." | Correcto pero genérico; cualquier competidor podría usarlo |
| "KIPUX — Tus impuestos, claros y ordenados." | Más específico, buena opción secundaria (subheadline) |
| "KIPUX — Contabilidad que se entiende." | Suena a Contablix/Countax; bajo diferencial |
| **"KIPUX — Automatizamos lo simple. Te acompañamos en lo importante."** | **Recomendado como tagline principal** — es el único que describe el modelo híbrido, que es el verdadero diferencial |
| "KIPUX — Del dato a la decisión." | Fuerte para fase 2 (visión de plataforma financiera), prematuro para el lanzamiento como estudio contable |

---

## 4. Arquitectura completa del sitio

Evalué la estructura de 13 secciones propuesta en el brief contra lo que muestran los cinco competidores relevados. Ajuste principal: separo **"Cómo funciona"** y **"Dashboard"** en páginas propias además de vivir como secciones de la home — todos los competidores con producto real (Tributo Simple, Gestorando) les dan jerarquía de página propia, no solo de sección scrolleable, porque son el argumento de venta más fuerte y necesitan su propia URL indexable. También agrego una página **"Sobre KIPUX"** explícita (el brief la pide en el punto 12 del entregable pero no en la arquitectura del punto 10) porque es donde vive la credencial profesional — crítica para la confianza (sección 25 del brief).

### 4.1 Arquitectura de navegación (sitio completo)

```text
KIPUX
│
├── Home (/)
├── Servicios (/servicios)
│   ├── Monotributo (/servicios/monotributo)
│   ├── Responsable Inscripto (/servicios/responsable-inscripto)
│   └── Casos complejos (/servicios/casos-complejos)
├── Cómo funciona (/como-funciona)
├── Precios (/precios)
├── Dashboard (/dashboard) — página de "producto", no funcional
├── Sobre KIPUX (/sobre-kipux)
├── Recursos (/recursos) — blog SEO, ver sección 20
│   └── /recursos/[slug]
├── Preguntas frecuentes (/preguntas-frecuentes)
├── Empezar / Onboarding (/empezar)
├── Contacto (/contacto)
├── Legales
│   ├── Términos y condiciones (/legales/terminos)
│   ├── Política de privacidad (/legales/privacidad)
│   └── [COMPLETAR con matrícula/razón social, ver sección 22.9]
└── Footer (persistente en todas las páginas)
```

### 4.2 Navegación principal (header)

Máximo 5 ítems visibles + 1 CTA, siguiendo el patrón que mejor funciona entre los relevados (Tributo Simple):

```text
[Logo KIPUX]   Servicios   Cómo funciona   Precios   Recursos     [Iniciar sesión]  [Quiero empezar →]
```

"Iniciar sesión" queda como link secundario discreto (para cuando exista el dashboard funcional) — no compite con el CTA primario.

### 4.3 Jerarquía de páginas por prioridad de conversión

| Prioridad | Página | Función en el embudo |
|---|---|---|
| 1 | Home | Entender + decidir seguir |
| 2 | Precios | Filtrar por presupuesto |
| 3 | Empezar (onboarding) | Convertir |
| 4 | Cómo funciona | Resolver objeción "¿es confiable/fácil?" |
| 5 | Servicios | Confirmar que aplica a su caso |
| 6 | Preguntas frecuentes | Resolver última duda antes de convertir |
| 7 | Dashboard | Reforzar diferencial tecnológico |
| 8 | Sobre KIPUX | Resolver objeción de confianza/credencial |
| 9 | Recursos (blog) | Atraer tráfico frío (SEO) |
| 10 | Contacto | Ruta alternativa para quien no quiere autoservicio |

---

## 5. Sitemap

| URL | Página | Objetivo | Indexable |
|---|---|---|---|
| `/` | Home | Conversión general | Sí |
| `/servicios` | Servicios (overview) | Segmentar por tipo de contribuyente | Sí |
| `/servicios/monotributo` | Servicios — Monotributo | Capturar búsqueda de intención | Sí |
| `/servicios/responsable-inscripto` | Servicios — RI simple | Capturar búsqueda de intención | Sí |
| `/servicios/casos-complejos` | Servicios — Casos complejos | Derivar a consulta personalizada | Sí |
| `/como-funciona` | Proceso paso a paso | Bajar fricción/objeción | Sí |
| `/precios` | Planes y precios | Filtrar y convertir | Sí |
| `/dashboard` | Vitrina del producto | Diferenciación tecnológica | Sí |
| `/sobre-kipux` | Equipo, credenciales, origen del nombre | Confianza | Sí |
| `/recursos` | Blog / hub de contenido | Tráfico orgánico | Sí |
| `/recursos/[slug]` | Artículos individuales | Long-tail SEO | Sí |
| `/preguntas-frecuentes` | FAQ | Resolver objeciones | Sí |
| `/empezar` | Onboarding (flujo de pasos) | Conversión | No (o sí, evaluar con equipo SEO — ver 20.4) |
| `/contacto` | Formulario + WhatsApp + datos | Conversión alternativa | Sí |
| `/legales/terminos` | T&C | Cumplimiento | No necesario indexar, pero debe existir |
| `/legales/privacidad` | Privacidad | Cumplimiento | No necesario indexar, pero debe existir |

---

## 6. Wireframe textual de HOME

```text
┌─────────────────────────────────────────────────────────────┐
│ HEADER (sticky)                                              │
│ Logo | Servicios | Cómo funciona | Precios | Recursos        │
│                                    [Iniciar sesión] [Quiero empezar →] │
├─────────────────────────────────────────────────────────────┤
│ 1. HERO                                                       │
│    Headline + subheadline                                    │
│    [CTA primario: Quiero empezar]  [CTA secundario: Ver cómo funciona] │
│    Visual: mockup de dashboard + motivo khipu sutil de fondo  │
├─────────────────────────────────────────────────────────────┤
│ 2. EL PROBLEMA (agitación breve, 3 pain points con ícono)     │
├─────────────────────────────────────────────────────────────┤
│ 3. PROPUESTA DE VALOR (los 5 pilares, en 3-4 bloques visuales)│
├─────────────────────────────────────────────────────────────┤
│ 4. CÓMO FUNCIONA (proceso en 4 pasos, resumen — link a página completa) │
├─────────────────────────────────────────────────────────────┤
│ 5. PARA QUIÉN ES (grid de 5 perfiles + "¿situación más compleja?") │
├─────────────────────────────────────────────────────────────┤
│ 6. DASHBOARD (vitrina — mockup grande + 4 bullets de lo que ves) │
├─────────────────────────────────────────────────────────────┤
│ 7. SERVICIOS (3 cards: Monotributo / RI Simple / Casos complejos) │
├─────────────────────────────────────────────────────────────┤
│ 8. PRECIOS (preview de 3 planes + link a página completa)     │
├─────────────────────────────────────────────────────────────┤
│ 9. DIFERENCIALES (por qué KIPUX y no un estudio tradicional o una app) │
├─────────────────────────────────────────────────────────────┤
│ 10. CONFIANZA (credencial profesional + espacio preparado para testimonios) │
├─────────────────────────────────────────────────────────────┤
│ 11. FAQ (5-6 preguntas más frecuentes, preview — link a página completa) │
├─────────────────────────────────────────────────────────────┤
│ 12. CTA FINAL (banda de cierre, full width)                   │
├─────────────────────────────────────────────────────────────┤
│ FOOTER                                                        │
│ Logo + tagline | Navegación | Legales | Contacto | Redes      │
└─────────────────────────────────────────────────────────────┘
```

**Cambio respecto al orden propuesto en el brief:** subo "Para quién es" antes de "Servicios" y bajo "Casos complejos" a una mención dentro de esa misma sección en vez de un bloque separado — evita que la home se sienta larga y repetitiva (el brief tenía 13 bloques; este wireframe consolida a 12 sin perder contenido, moviendo detalle a páginas propias).

---

## 7. Copy completo de HOME

*(Hero: ver sección 8 — se desarrollan 3 alternativas ahí; acá sigue el resto de la home con la alternativa de hero recomendada ya insertada.)*

### 1. Hero — ver sección 8 (Alternativa A, recomendada)

### 2. El problema

**Eyebrow:** Si esto te suena familiar

**Título:** Tu contador te manda un PDF una vez al mes. Y el resto del tiempo, no sabés nada.

**Los tres dolores:**

- **No sabés si estás al día.** Te enterás de un vencimiento cuando ya casi venció — o cuando ya venció.
- **No entendés qué estás pagando.** Los números aparecen, pero nadie te explica de dónde salen.
- **Preguntar es un via crucis.** Un mensaje de WhatsApp que tarda tres días en tener respuesta, para algo que debería tardar tres segundos.

**Cierre de sección:** No es que tu contador sea malo. Es que el modelo — todo manual, todo por WhatsApp — no escala. Por eso lo cambiamos.

### 3. Propuesta de valor

**Título:** Automatizamos lo simple. Te acompañamos en lo importante.

**Cuerpo:** KIPUX se ocupa de lo repetitivo — vencimientos, liquidaciones, alertas — con tecnología. Y pone a una contadora matriculada a resolver lo que de verdad requiere criterio: tu categoría, tus excepciones, tus dudas. Vos ves todo en un solo lugar, en tiempo real.

**4 pilares (formato de cards):**

| Pilar | Copy |
|---|---|
| Simplicidad | Sin lenguaje técnico. Si hace falta una acción, te lo decimos en una frase. |
| Tecnología | Tu situación fiscal, siempre visible — no una vez al mes, sino ahora. |
| Transparencia | Sabés qué pagás y por qué, antes de que te lo preguntemos nosotros. |
| Respaldo profesional | Cada caso lo revisa una contadora matriculada. No hay una IA firmando por vos. |

### 4. Cómo funciona (resumen)

**Título:** De acá a que dejes de pensar en impuestos, hay 4 pasos.

1. **Contás tu situación** — un formulario de 3 minutos, no una planilla de Excel.
2. **Ordenamos** — revisamos tu situación fiscal actual y te decimos exactamente dónde estás parado.
3. **Automatizamos** — tus obligaciones periódicas quedan en piloto automático, con alertas antes de cada vencimiento.
4. **Vos mirás el dashboard** — y listo. Si hace falta que hagas algo, te lo decimos ahí y por WhatsApp.

**CTA de sección:** Ver el proceso completo →

### 5. Para quién es

**Título:** ¿Sos alguno de estos?

| Perfil | Descripción corta |
|---|---|
| Monotributista | Facturás, pagás, y querés dejar de pensarlo. |
| Emprendedor | Estás por arrancar y necesitás hacer las cosas bien desde el día uno. |
| Profesional independiente | Diseñador, arquitecto, abogado, programador, consultor — necesitás delegar la parte fiscal sin perder el control. |
| Freelancer | Cobrás en pesos, en dólares, o en las dos — y necesitás que alguien lo ordene. |
| Pequeño comercio | IVA, Ingresos Brutos, facturación — todo en un solo lugar. |

**Bloque complementario:**

**Título:** ¿Tu situación es más compleja?

**Cuerpo:** Si tenés empleados, sociedad, más de una actividad o estás en medio de una fiscalización, también podemos ayudarte — con atención profesional dedicada y un presupuesto a medida. [Contanos tu caso →]

### 6. Dashboard (vitrina)

**Título:** Tu situación fiscal, en un solo lugar. En serio.

**Cuerpo:** Nada de buscar el último PDF que te mandaron por WhatsApp. Entrás y en cinco segundos sabés si está todo en orden, cuánto tenés que pagar y cuándo.

**4 bullets junto al mockup:**
- Estado fiscal en tiempo real
- Cuánto pagás y cuándo vence — sin sorpresas
- Documentación: qué falta y qué ya está
- Historial completo, siempre a mano

**CTA de sección:** Ver el dashboard en detalle →

*(Nota: el dashboard mostrado en la web es una vitrina — mockup con datos ficticios, no el producto funcional. Desarrollo del dashboard real queda en Fase 2, ver sección 23.)*

### 7. Servicios

**Título:** Un plan para cada tipo de contribuyente.

**3 cards:**

| Servicio | Para quién | CTA |
|---|---|---|
| Monotributo | Monotributistas simples y con mayor actividad | Ver plan → |
| Responsable Inscripto simple | RI de baja complejidad | Ver plan → |
| Casos complejos | Pymes, sociedades, fiscalizaciones | Consultar → |

### 8. Precios

**Título:** Precios claros. Sin letra chica.

**Cuerpo:** Vas a saber exactamente qué pagás y qué incluye, antes de decidir. Nada de "a cotizar" después de una llamada de 30 minutos.

*(Preview de 3 planes — copy completo en sección 10.)*

**CTA de sección:** Ver todos los planes →

### 9. Diferenciales

**Título:** Por qué KIPUX y no otra opción

| No un estudio tradicional | No una app de autogestión |
|---|---|
| Vas a ver tu situación en tiempo real, no una vez al mes | Cada caso lo revisa una contadora matriculada — no estás solo con un formulario |
| Vencimientos con alerta previa, no un mensaje después de que ya pasó | Si tu situación se complica, hay alguien con criterio profesional para resolverlo |
| Precio claro desde el principio | Respaldo real ante ARCA/BCRA — no un bot respondiendo preguntas normativas |

### 10. Confianza

**Título:** Quién está detrás de KIPUX

**Cuerpo:** KIPUX está dirigido por `[COMPLETAR: nombre + matrícula profesional]`, Contadora Pública, con base en Tucumán. Cada declaración, cada presentación y cada respuesta la revisa una profesional matriculada — no un algoritmo.

**Bloque de credenciales (a completar):**
- Matrícula profesional: `[COMPLETAR]`
- Consejo Profesional: `[COMPLETAR]`
- Ubicación: `[COMPLETAR — dirección o "San Miguel de Tucumán"]`

**Espacio de testimonios (preparado, sin contenido inventado):**
> "Acá van los primeros testimonios de clientes reales de KIPUX. Recomendación: activar este bloque recién con 5-8 testimonios genuinos — mientras tanto, reemplazar por el bloque de credenciales + FAQ, que cumple la misma función de reducir objeciones."

### 11. FAQ (preview — 5 preguntas, copy completo en sección 14)

*(ver sección 14 para el listado completo; en home se muestran las 5 marcadas como "home" en esa tabla)*

**CTA de sección:** Ver todas las preguntas →

### 12. CTA final

**Título:** Dejá de perseguir tus vencimientos. Que te persigan a vos las buenas noticias.

**Subtítulo:** Empezar te lleva 3 minutos. No hay compromiso hasta que veas tu situación ordenada.

**CTA primario:** Quiero empezar →
**CTA secundario:** Hablar con KIPUX (WhatsApp)

### Footer

```text
KIPUX
Automatizamos lo simple. Te acompañamos en lo importante.

Navegación          Servicios              Legales
Home                 Monotributo            Términos y condiciones
Cómo funciona        Responsable Inscripto  Política de privacidad
Precios              Casos complejos        [COMPLETAR: matrícula/CUIT]
Recursos
Preguntas frecuentes

Contacto
[COMPLETAR: email]
[COMPLETAR: WhatsApp]
San Miguel de Tucumán, Argentina

[Instagram] [LinkedIn] [WhatsApp]

© 2026 KIPUX. Todos los derechos reservados.
```

---

## 8. Tres alternativas de Hero

### Alternativa A — "Modelo híbrido" (★ Recomendada)

- **Headline:** Automatizamos lo simple. Te acompañamos en lo importante.
- **Subheadline:** KIPUX es tu estudio contable digital: vencimientos, liquidaciones y alertas en piloto automático — con una contadora matriculada resolviendo lo que realmente lo necesita.
- **CTA primario:** Quiero empezar
- **CTA secundario:** Ver cómo funciona
- **Idea visual:** Mockup del dashboard (card "Estado fiscal: OK", monto a pagar, próximo vencimiento) flotando sobre un fondo con líneas finas tipo khipu que conectan puntos de datos — sutil, sin iconografía andina literal.
- **Justificación estratégica:** Es el hero que mejor traduce la tesis de posicionamiento (sección 3.1). Ningún competidor relevado puede usar este headline sin mentir: Contablix y Countax no automatizan de cara al cliente, Gestorando y Tributo Simple no tienen contador matriculado como parte central del mensaje. Es el más defendible a largo plazo porque describe el modelo, no una promesa vacía.

### Alternativa B — "Directo al dolor"

- **Headline:** Dejá de enterarte de tus vencimientos tarde.
- **Subheadline:** KIPUX te muestra tu situación fiscal en tiempo real y te avisa antes — no después. Todo con respaldo profesional real.
- **CTA primario:** Quiero empezar
- **CTA secundario:** Ver precios
- **Idea visual:** Comparación lado a lado: a la izquierda, un chat de WhatsApp desordenado con mensajes tardíos; a la derecha, la card de "próximo vencimiento" del dashboard de KIPUX, limpia y con alerta previa.
- **Justificación estratégica:** Más agresivo en conversión inmediata — apela directo al pain point #1 relevado en las personas del brief. Funciona mejor en campañas pagas (Google/Meta) que como headline institucional de home, porque agota su efecto rápido y no deja lugar para comunicar el diferencial de "respaldo profesional" con la misma fuerza que la Alternativa A.

### Alternativa C — "Conceptual / marca"

- **Headline:** Tus datos fiscales, ordenados. Tus decisiones, claras.
- **Subheadline:** KIPUX transforma información dispersa en algo que se entiende de un vistazo — con la tecnología de una fintech y el criterio de una contadora matriculada.
- **CTA primario:** Quiero empezar
- **CTA secundario:** Conocer KIPUX
- **Idea visual:** Animación sutil de líneas/nudos (referencia al khipu) que se reorganizan de un patrón caótico a uno ordenado al cargar la página — metáfora visual literal de "del dato a la decisión".
- **Justificación estratégica:** Es el hero con más personalidad de marca y el que mejor explota el concepto khipu (sección 21 del brief), pero es el más arriesgado para un lanzamiento: exige que el visitante infiera el beneficio concreto, y el brief pide evitar headlines que no se entiendan en segundos (regla 7). Mejor candidato para la página "Sobre KIPUX" o para una campaña de marca en fase 2, no para el hero de lanzamiento.

**Recomendación final:** Alternativa A para el lanzamiento. Si en los primeros meses el dato de conversión muestra que el mensaje "modelo híbrido" no está calando (por ejemplo, alta tasa de rebote en el hero medida con scroll depth), testear la Alternativa B como variante A/B — es la que más se acerca a conversión inmediata sin resignar el mensaje de respaldo profesional en el subheadline.

---

## 9. Página de Servicios — Copy completo

**URL:** `/servicios`
**Title tag:** Servicios contables para monotributistas y pymes | KIPUX
**H1:** Un servicio para cada tipo de contribuyente

**Intro:** No vendemos "planes de contador" genéricos. Cada servicio de KIPUX está armado para un tipo de situación fiscal específica — así el precio y el trabajo que hacemos tienen sentido para lo que realmente necesitás.

### Bloque 1 — Monotributo

**H2:** Para monotributistas
**Copy:** Si facturás como monotributista, KIPUX se ocupa de que tu categoría esté siempre bien, tus pagos estén al día y no te llegue ninguna sorpresa. Vas a ver en tu dashboard exactamente cuánto pagás, cuándo, y por qué.

**Incluye (lista, ejemplo — validar alcance final con Mariana):**
- Monitoreo de facturación y categoría
- Alertas de vencimiento con anticipación
- Recategorización cuando corresponde
- Dashboard con estado fiscal en tiempo real
- Soporte por WhatsApp para excepciones

**CTA:** Ver plan Monotributo →

### Bloque 2 — Responsable Inscripto simple

**H2:** Para responsables inscriptos de baja complejidad
**Copy:** Si sos RI pero tu operación es relativamente simple — IVA, Ingresos Brutos, sin gran estructura societaria — KIPUX estandariza tus declaraciones periódicas y te muestra tu situación sin que tengas que pedirla.

**Incluye (ejemplo):**
- Liquidación de IVA e Ingresos Brutos
- Declaraciones juradas periódicas
- Control fiscal y alertas
- Dashboard con historial completo

**CTA:** Ver plan RI Simple →

### Bloque 3 — Casos complejos

**H2:** ¿Tu situación no entra en lo simple?
**Copy:** Pymes, sociedades, más de una actividad, fiscalizaciones o inspecciones en curso: seguimos pudiendo ayudarte, pero con otro modelo — atención profesional personalizada y presupuesto a medida, sin intentar meter tu caso en un molde que no le queda.

**Incluye:**
- Diagnóstico inicial de tu situación
- Atención directa con contadora matriculada
- Presupuesto a medida, sin sorpresas
- Acompañamiento en fiscalizaciones e inspecciones

**CTA:** Contanos tu caso →

*(Nota para desarrollo: cada bloque debería tener también su propia URL — `/servicios/monotributo`, etc. — con el mismo copy expandido a página completa para SEO. Ver sitemap, sección 5.)*

---

## 10. Página de Pricing — Copy completo

**URL:** `/precios`
**Title tag:** Precios claros para tu monotributo o RI | KIPUX
**H1:** Precios claros. Sin letra chica.
**Subheadline:** Sabés exactamente qué pagás y qué incluye antes de decidir. Si tu caso es más complejo, te lo decimos de entrada — no después de la tercera reunión.

### Estructura de planes recomendada

Mantengo el naming del material de proyecto (es claro y ya está validado internamente) con un ajuste: agrego una etiqueta de "para quién es" en una frase, que ningún competidor relevado hace bien.

| Plan | Para quién | Precio | Incluye (a validar alcance final) |
|---|---|---|---|
| **KIPUX Mono Básico** | Monotributista sin empleados, actividad simple | Desde `[COMPLETAR: $X]/mes` | Monitoreo de categoría, alertas de vencimiento, dashboard, soporte digital básico |
| **KIPUX Mono Plus** | Monotributista con mayor actividad o facturación más alta | Desde `[COMPLETAR: $X]/mes` | Todo lo anterior + control de facturación, recategorizaciones, reporte mensual, soporte prioritario |
| **KIPUX RI Simple** | Responsable Inscripto de baja complejidad | Desde `[COMPLETAR: $X]/mes` | IVA, Ingresos Brutos, declaraciones periódicas, dashboard, alertas, historial |
| **Casos especiales** | Pymes, sociedades, fiscalizaciones | A presupuestar | Diagnóstico + atención dedicada + presupuesto a medida |

**Extras (se cobran aparte, no están en el abono — evita la trampa de "todo incluido = trabajo ilimitado"):**
- Recategorizaciones fuera de lo previsto
- Altas y bajas
- Planes de pago
- Liquidación de sueldos (si hay empleados)
- Fiscalizaciones e inspecciones
- Regularizaciones y trabajos retroactivos
- Asesoramiento estratégico / planeamiento fiscal

**Nota abajo de la tabla (copy real):**
> Los precios son por contribuyente y varían según categoría y volumen de actividad. Vas a ver el precio exacto para tu caso en el paso 3 del onboarding, antes de confirmar nada.

### Por qué mostrar precios en la web (decisión y fundamento)

Decisión: **sí, mostrar un piso de precio por plan ("desde $X"), no un precio cerrado único.**

- Contablix esconde el precio detrás de una cotización — genera fricción y contradice el mensaje de transparencia.
- Gestorando y Tributo Simple muestran precio fijo, pero son autoservicio puro (sin contador matriculado revisando cada caso), así que su modelo de precio único es más fácil de sostener.
- KIPUX tiene trabajo profesional real detrás, con variación legítima según categoría/volumen — un precio único sería o bien inexacto, o bien fijado tan alto que pierde el ancla de "accesible".
- La solución intermedia — mostrar un piso claro por plan + explicitar que el precio final se confirma en el onboarding — cumple la promesa de transparencia sin comprometer el margen en casos atípicos.

**Referencia de mercado relevada** (no son precios de KIPUX, son anclas de lo que cobran otros jugadores del segmento, útiles para fijar los precios reales): Gestorando premium ronda $13.000 cada 3 meses (~$4.300/mes); Tributo Simple cobra $17.500/mes en su nivel de integraciones; Lannis cobra USD 25/mes dirigido a un segmento distinto (ingresos en moneda extranjera). Ninguno de los tres incluye revisión de una contadora matriculada por caso — KIPUX puede y debería cobrar más que estos pisos, justificado por ese respaldo. La definición del número final requiere el estudio de unit economics que el material de proyecto ya identifica como pendiente (Fase 0, punto C del roadmap original).

**CTA de página:** Quiero empezar →

---

## 11. Página "Cómo funciona" — Copy completo

**URL:** `/como-funciona`
**Title tag:** Cómo funciona KIPUX — estudio contable digital | KIPUX
**H1:** De acá a que dejes de pensar en impuestos, hay 5 pasos

Reviso el proceso propuesto en el brief (5 pasos: Te registrás / Ordenamos / Automatizamos / Vos ves todo / Te avisamos) y lo mantengo con un cambio: invierto el orden de los pasos 4 y 5 — "te avisamos" tiene que pasar *antes* de que el cliente tenga que ir a mirar el dashboard, no después. La secuencia real de valor es "te avisamos → vas, mirás, resolvés", no al revés.

### Paso 1 — Contás tu situación
**Copy:** Un formulario de 3 minutos: quién sos, qué actividad tenés, si ya estás inscripto o estás arrancando. Nada de subir veinte archivos todavía.

### Paso 2 — Ordenamos
**Copy:** Revisamos tu situación fiscal actual — categoría, vencimientos pendientes, documentación existente — y te decimos exactamente dónde estás parado. Si hay algo desordenado, te lo mostramos con claridad, no con jerga.

### Paso 3 — Automatizamos
**Copy:** Tus obligaciones periódicas quedan en piloto automático: liquidaciones, presentaciones, cálculo de lo que corresponde pagar cada mes.

### Paso 4 — Te avisamos
**Copy:** Antes de cada vencimiento — no después — te llega una alerta con lo que tenés que hacer y cuánto tenés que pagar.

### Paso 5 — Vos ves todo
**Copy:** Entrás a tu dashboard cuando quieras y ves tu estado fiscal completo: al día, en revisión, o con algo pendiente. Sin tener que preguntar.

### Bloque adicional — "¿Y si mi caso no es simple?"
**Copy:** Si en el paso 2 detectamos que tu situación tiene más complejidad de la esperada — empleados, sociedad, una inspección en curso — te lo decimos ahí mismo y pasás a atención personalizada, con presupuesto a medida. No seguís un proceso automatizado que no te sirve.

**CTA final de página:** Quiero empezar →

---

## 12. Página "Sobre KIPUX" — Copy completo

**URL:** `/sobre-kipux`
**Title tag:** Sobre KIPUX — estudio contable digital en Tucumán
**H1:** Por qué existe KIPUX

**Bloque 1 — Origen (breve, sin caer en lo folclórico):**
**Copy:** El nombre KIPUX viene del *khipu*, el sistema que usaban las civilizaciones andinas para registrar información con cuerdas y nudos — una de las formas más antiguas de organizar datos para tomar decisiones. Hoy hacemos lo mismo con tu situación fiscal: tomamos información dispersa y la convertimos en algo claro, ordenado y accionable.

**Bloque 2 — Por qué un estudio digital:**
**Copy:** Empezamos en Tucumán porque acá es donde conocemos el contexto: el tipo de contribuyente, la relación con los organismos provinciales, lo que realmente le pasa a un monotributista local. La tecnología nos permite ofrecer un servicio con la eficiencia de una fintech, sin perder eso.

**Bloque 3 — Quién está detrás (credencial):**
**Copy:** KIPUX está dirigido por `[COMPLETAR: nombre completo]`, Contadora Pública (matrícula `[COMPLETAR]`, `[COMPLETAR: Consejo Profesional correspondiente]`). Cada declaración y cada presentación de un cliente de KIPUX la revisa una profesional matriculada — no un sistema automático sin supervisión.

**Bloque 4 — Cómo trabajamos:**
**Copy:** Automatizamos lo repetitivo para que el tiempo profesional se use donde realmente aporta: interpretar tu caso, resolver excepciones, y acompañarte cuando la situación se complica. La tecnología no reemplaza el criterio de un contador — lo libera para las cosas en las que un contador realmente importa.

**Bloque 5 — Hacia dónde vamos (visión, tono medido):**
**Copy:** Hoy somos un estudio contable digital. La idea es que, con el tiempo, KIPUX sea el lugar donde un pequeño contribuyente entiende y gestiona toda su relación con el fisco — no solo sus impuestos.

**CTA de página:** Quiero empezar →

---

## 13. Página de Contacto / Onboarding — Copy completo

### 13.1 Página de contacto (`/contacto`)

**H1:** Hablemos
**Copy:** Si preferís contarnos tu situación antes de arrancar el proceso online, elegí el canal que te quede más cómodo.

**Opciones:**
- **WhatsApp** — Respuesta en el día. `[COMPLETAR: número]`
- **Email** — `[COMPLETAR: dirección]`
- **Formulario** — nombre, email, teléfono, tipo de contribuyente (select), mensaje libre (opcional)

**Nota de expectativa (reduce ansiedad, siguiendo el mejor patrón relevado en Contablix):** Escribirnos no te compromete a nada. Es solo la forma más rápida de que te digamos si KIPUX es para vos.

### 13.2 Flujo de Onboarding (`/empezar`)

Reviso el flujo de 5 pasos propuesto en el brief. Lo simplifico a 4 — fusiono "qué necesitás" dentro del primer paso, porque preguntarlo por separado agrega una pantalla sin agregar información que no se pueda inferir del tipo de contribuyente + un campo de texto libre.

**Progreso visible en todo momento:** `Paso 1 de 4`

#### Paso 1 — ¿Qué tipo de contribuyente sos?

**Copy:** Así sabemos qué mostrarte después.

- Monotributista
- Responsable Inscripto
- Todavía no estoy inscripto / estoy arrancando
- No estoy seguro — ayudame a saber

*(La última opción no descarta a nadie del embudo: dirige a un mini-cuestionario de 2 preguntas — "¿facturás actualmente?" / "¿tenés CUIT?" — que infiere la categoría probable.)*

#### Paso 2 — Contanos tu situación actual

**Copy:** Sin vueltas: ¿cómo está tu situación fiscal hoy?

- Estoy al día
- Tengo algo pendiente o atrasado
- No sé cómo estoy — quiero que alguien lo revise
- Tengo otro contador y quiero cambiarme a KIPUX

*(Cada opción alimenta el mensaje que ve el cliente en el paso 4 — ver más abajo.)*

#### Paso 3 — Tus datos básicos

**Campos:** Nombre y apellido, CUIT (opcional en este paso si "no estoy inscripto"), email, WhatsApp, actividad/rubro (texto libre o select).

**Microcopy debajo del formulario:** Con esto no te damos de alta en nada todavía. Es lo que necesitamos para armar tu diagnóstico.

#### Paso 4 — Confirmación y siguiente paso

**Copy dinámico según respuesta del Paso 2:**

| Si eligió | Mensaje de cierre |
|---|---|
| Estoy al día | Perfecto — te contactamos en menos de 24hs con tu plan sugerido y precio exacto. |
| Tengo algo pendiente | Te vamos a contactar primero para entender qué falta resolver, antes de hablar de plan. |
| No sé cómo estoy | Una contadora de KIPUX va a revisar tu caso antes de sugerirte nada — sin costo por este primer diagnóstico. |
| Tengo otro contador | Sin problema — te ayudamos con la transición. Te contactamos para coordinar el cambio. |

**CTA final:** Listo, ¿qué sigue? → *(WhatsApp directo + expectativa de tiempo de respuesta)*

---

## 14. Preguntas frecuentes — Copy completo

**URL:** `/preguntas-frecuentes`
**H1:** Preguntas frecuentes
*(Las marcadas "Home" se muestran también como preview en la sección 11 de la home.)*

| # | Pregunta | Respuesta | En Home |
|---|---|---|---|
| 1 | ¿Qué es KIPUX exactamente? | Un estudio contable digital: automatizamos tus obligaciones periódicas y te mostramos tu situación fiscal en tiempo real, con una contadora matriculada revisando cada caso. | Sí |
| 2 | ¿Cuánto cuesta? | Depende de tu categoría y actividad. Los planes arrancan desde `[COMPLETAR]`/mes — vas a ver el precio exacto para tu caso antes de confirmar nada. | Sí |
| 3 | ¿Qué incluye el abono mensual? | Monitoreo de tu situación, liquidaciones periódicas, alertas de vencimiento y acceso al dashboard. Trámites extraordinarios (altas, planes de pago, fiscalizaciones) se cotizan aparte — así el abono se mantiene predecible. | Sí |
| 4 | Ya tengo un contador. ¿Puedo cambiarme a KIPUX? | Sí. Nos encargamos de coordinar la transición — vos solo tenés que avisarle a tu contador actual que vas a cambiar. | Sí |
| 5 | Estoy atrasado con mis presentaciones. ¿KIPUX me puede ayudar igual? | Sí. En el diagnóstico inicial identificamos qué está pendiente y armamos un plan para ponerte al día antes de pasar al esquema mensual normal. | Sí |
| 6 | ¿Qué documentación necesito para empezar? | Para el diagnóstico inicial, con tu CUIT y clave fiscal alcanza. Documentación adicional (facturación, comprobantes) te la vamos pidiendo puntualmente desde el dashboard. | No |
| 7 | Tengo empleados. ¿Pueden llevar la liquidación de sueldos? | Sí, como servicio adicional al plan base — se cotiza según cantidad de empleados. | No |
| 8 | Soy Responsable Inscripto, no monotributista. ¿KIPUX me sirve? | Sí, si tu operación es de baja-media complejidad (IVA, Ingresos Brutos, sin gran estructura societaria) — es el plan KIPUX RI Simple. Para estructuras más grandes, trabajamos con presupuesto a medida. | No |
| 9 | Vivo fuera de Tucumán, ¿igual puedo ser cliente? | Sí — el servicio es 100% digital. Empezamos en Tucumán por cercanía y conocimiento del contexto local, pero no es un requisito para ser cliente. | No |
| 10 | ¿Cómo me contacto con la contadora si tengo una duda puntual? | Por WhatsApp, dentro de tu plan. Las consultas de rutina las resuelve el dashboard; las que necesitan criterio profesional las responde directamente el equipo. | No |
| 11 | ¿Qué pasa si me llega una inspección o fiscalización? | Te acompañamos con atención profesional dedicada. No es parte del abono mensual estándar — se cotiza según el caso, porque cada fiscalización es distinta. | No |
| 12 | ¿Cómo funciona el dashboard? | Es tu panel personal: estado fiscal, cuánto pagás y cuándo, documentación pendiente e historial completo. Se actualiza automáticamente, no tenés que pedirle nada a nadie para verlo. | Sí |
| 13 | ¿Cómo pago mis impuestos? | KIPUX te dice cuánto y cuándo, con la información lista para pagar (VEP u orden de pago según el impuesto). El pago en sí lo hacés vos, como con cualquier contador — por ahora KIPUX no procesa el pago en tu nombre. | No |
| 14 | ¿Mis datos están seguros? | Sí — usamos los mismos estándares de seguridad que cualquier plataforma financiera para el manejo de tu información. `[COMPLETAR: detalle técnico de seguridad cuando exista infraestructura definida]` | No |
| 15 | ¿Puedo cancelar cuando quiera? | Sí, no hay permanencia mínima. `[COMPLETAR: confirmar política real de baja antes de publicar]` | No |

**CTA final de página:** ¿No encontraste tu pregunta? Escribinos por WhatsApp →

---

## 15. Dashboard preview — definición visual y funcional

**Importante (repetido del brief, remarcado porque afecta el scope de desarrollo):** lo que se construye para la web pública es una **vitrina** — un mockup con datos ficticios, no el dashboard funcional. El dashboard real es un desarrollo de producto aparte (Fase 2/3, ver sección 23).

### 15.1 Dónde vive en el sitio

- Versión reducida embebida en el hero (Alternativa A de hero, sección 8).
- Versión ampliada en la sección 6 de la home.
- Página propia `/dashboard` con la versión completa + explicación de cada bloque.

### 15.2 Qué debe mostrar la vitrina (mapeado 1 a 1 con el material de proyecto, sección 10-11 del doc cargado)

```text
┌──────────────────────────────────────────────┐
│ KIPUX                    🟢 Todo en orden     │
│ Hola, Juan                                    │
├──────────────────────────────────────────────┤
│ TOTAL A PAGAR ESTE MES                        │
│ $57.000                                       │
│ Próximo vencimiento: 20/01 — Monotributo      │
├──────────────────────────────────────────────┤
│ IMPUESTOS                                     │
│ Monotributo     $45.000    20/01    🟢        │
│ IIBB            $12.000    22/01    🟡        │
├──────────────────────────────────────────────┤
│ DOCUMENTACIÓN                                 │
│ ✔ Facturación cargada                         │
│ ✔ Pagos informados                            │
│ ⬆ Falta: comprobante bancario                 │
├──────────────────────────────────────────────┤
│ HISTORIAL                                     │
│ Dic 2025  ✔ Pagado                            │
│ Nov 2025  ✔ Pagado                            │
└──────────────────────────────────────────────┘
```

### 15.3 Reglas de diseño de la vitrina (heredadas del material de proyecto, sección 14 y 11.5)

- **3 estados posibles**, sin ambigüedad visual: 🟢 Todo en orden / 🟡 Atención / 🔴 Acción requerida.
- Cada alerta debe llevar una acción concreta al lado (ej: "Ver qué hacer"), nunca informar sin dar un siguiente paso.
- No mostrar PDFs como formato principal, ni lenguaje técnico-contable, ni detalle contable interno (eso es para la vista interna del contador, no la del cliente).
- El total a pagar y el próximo vencimiento van siempre arriba de todo — son los dos datos que un usuario busca primero (principio "5 segundos" del material de proyecto).

### 15.4 Cómo se anima/interactúa en la web (sin ser el producto real)

- Al hacer scroll hasta la sección, las cards aparecen con una animación breve tipo "conexión de nodos" (líneas finas que se trazan entre los bloques) — refuerzo sutil del concepto khipu sin ilustrarlo literalmente.
- Un toggle simple "Ver en mobile / Ver en desktop" sobre el mismo mockup, para comunicar que el producto real es mobile-first sin necesitar dos secciones separadas.
- Nada de esto requiere backend: es HTML/CSS/JS con datos hardcodeados.

---

## 16. Sistema de CTAs

### 16.1 Jerarquía

| Nivel | CTA | Dónde aparece |
|---|---|---|
| Primario (único, repetido) | **Quiero empezar** | Header, hero, CTA final de cada página, banda de cierre de home |
| Secundario | Ver cómo funciona / Ver precios / Hablar con KIPUX (WhatsApp) | Hero, cierre de secciones intermedias |
| Terciario | Ver servicios / Ver plan [X] / Contanos tu caso | Dentro de cards y bloques específicos |

**Regla:** nunca dos CTAs primarios visibles al mismo tiempo en una misma vista. El primario compite solo con un secundario, nunca con otro primario.

### 16.2 Por qué "Quiero empezar" y no otra alternativa

Evalué contra "Empezar ahora" (Tributo Simple usa "Comenzá HOY") y "Cotizá tu servicio" (Contablix). "Quiero empezar" en primera persona genera más compromiso percibido que un imperativo genérico, sin la fricción de "cotizar" (que implica que todavía no hay compromiso ni claridad de precio — contradice la promesa de transparencia).

### 16.3 Formularios — qué pedir y cuándo

| Momento | Qué se pide | Por qué recién ahí |
|---|---|---|
| Antes de "Quiero empezar" | Nada | Cualquier dato pedido antes de que el usuario decida entrar es fricción pura |
| Onboarding paso 1-2 | Tipo de contribuyente + situación actual | Son preguntas de clasificación, no de contacto — bajan la guardia |
| Onboarding paso 3 | Nombre, CUIT (opcional), email, WhatsApp, actividad | Recién acá se pide contacto — después de que ya invirtió 2 pasos |
| Contacto directo (`/contacto`) | Nombre, email, teléfono, mensaje | Camino alternativo para quien no quiere el flujo guiado |

### 16.4 WhatsApp

Canal secundario visible en todo momento (icono flotante o link en header/footer), pero **no** reemplaza al flujo de onboarding como camino principal — WhatsApp es para quien prefiere hablar antes de decidir, el formulario es el camino que escala.

---

## 17. User journey

```text
VISITA (Google / Instagram / referido)
   ↓
ENTIENDE KIPUX → Hero + sección "El problema" resuelven esto en <10 segundos
   ↓
SE IDENTIFICA → Sección "Para quién es" — "sí, esto es para mí"
   ↓
CONOCE EL MODELO → "Cómo funciona" — entiende qué hace la máquina y qué hace la contadora
   ↓
CONOCE PRECIO → Sección/página de precios — filtra por presupuesto
   ↓
CONFÍA → Dashboard (ve el producto) + Sobre KIPUX (ve la credencial) + FAQ (resuelve la última duda)
   ↓
INICIA → CTA "Quiero empezar"
   ↓
ONBOARDING → 4 pasos, ~3-5 minutos
   ↓
CONTACTO HUMANO → WhatsApp/email en <24hs con diagnóstico y precio confirmado
```

**Puntos de fuga más probables (para monitorear con analytics desde el día 1):** entre "Conoce precio" y "Confía" — si no hay suficiente prueba social todavía (sección 6.6), y entre "Inicia" y "Onboarding completo" — el formulario de 4 pasos es corto, pero hay que medir abandono paso por paso.

---

## 18. Identidad visual

**Posicionamiento estético buscado:** entre fintech, SaaS y estudio profesional — nunca banco tradicional, nunca estudio jurídico, nunca artesanía andina literal.

### 18.1 Paleta cromática

| Rol | Color propuesto | Uso |
|---|---|---|
| Primario | Índigo profundo `#1E2A4A` | Header, textos de alto peso, fondos oscuros puntuales |
| Primario alternativo (fondos claros) | Blanco roto `#FAFAF7` | Fondo base de todas las páginas |
| Acento principal | Terracota cálido `#C4693B` | CTA primario, hitos de datos (montos, estados destacados) |
| Acento secundario | Verde estado OK `#3D9970` | Estado fiscal "todo en orden" |
| Alerta | Ámbar `#D9A441` | Estado "atención" |
| Error/urgente | Rojo terracota `#C1443C` | Estado "acción requerida" — nunca rojo puro de alarma bancaria |
| Texto secundario | Gris grafito `#5B5F6B` | Cuerpo de texto, subtítulos |

**Por qué esta paleta y no una paleta "tech" fría (azules eléctricos + blanco puro):** el terracota como acento es el único guiño cromático al textil andino (tonos de lana/tierra) sin volverse literal — cumple la regla 21 del brief ("sutil, conceptual, contemporáneo"). El índigo profundo en vez de azul SaaS genérico evita que KIPUX se vea como un clon de cualquier fintech internacional.

### 18.2 Tipografía

- **Titulares:** una sans-serif geométrica con carácter (ej. Söhne, General Sans, o Inter Display en su variante más ancha) — transmite tecnología sin frialdad.
- **Cuerpo de texto:** Inter o Manrope — máxima legibilidad, ya probada en dashboards y paneles de datos.
- **Cifras/dashboard:** una tabular figures variant (Inter tiene) para que los montos alineen perfectamente en las cards — detalle que un estudio contable tradicional nunca cuida y que comunica "producto" de inmediato.

### 18.3 Estilo fotográfico

- Nada de bancos de imágenes con "gente en oficina estrechando manos" (cliché de estudio contable/jurídico).
- Si se usan fotos: personas reales del segmento objetivo (emprendedores, profesionales independientes) en contextos cotidianos — no posados corporativos.
- Alternativa recomendada para el lanzamiento (más barata y más consistente): ilustración plana simple + el propio dashboard como "hero visual" en la mayoría de las secciones, minimizando la dependencia de fotografía.

### 18.4 Iconografía, formas, bordes, botones, cards

| Elemento | Especificación |
|---|---|
| Iconos | Trazo fino (1.5-2px), geométricos, sin relleno — familia consistente (ej. Phosphor o Lucide) |
| Bordes de card | Radio moderado (12-16px) — ni cuadrado (frío) ni muy redondeado (infantil) |
| Botones primarios | Radio 8-10px, terracota sólido, sin sombras duras |
| Botones secundarios | Outline, índigo, fondo transparente |
| Espaciado | Sistema de 8px base; generoso whitespace — evita la sensación "apretada" típica de sitios de estudios contables tradicionales |
| Sombras | Muy sutiles, difusas (`0 4px 24px rgba(30,42,74,0.08)`) — solo en cards de dashboard, nunca en botones |

### 18.5 Animaciones y microinteracciones

- Transiciones de 150-250ms, ease-out — nada de rebotes ni animaciones largas.
- El motivo khipu (líneas que conectan puntos de datos) se reserva para 2-3 momentos clave: hero, sección dashboard, y transición de carga entre pasos del onboarding. Usarlo en todas partes lo banaliza.
- Microinteracción recomendada en el dashboard-vitrina: al hacer hover sobre un ítem de "Impuestos", la línea que lo conecta con el estado general se resalta — refuerza la metáfora de "todo está conectado y trazable" sin decirlo con palabras.

### 18.6 Referencia al khipu — aplicación concreta

Evalúo las opciones planteadas en el brief (regla 21) y elijo dos, descartando el resto por riesgo de literalidad:

| Opción | Uso |
|---|---|
| Líneas que conectan puntos de datos | ✅ Adoptada — es la más flexible y la que mejor traduce "organizar información" a interfaz |
| Patrón de nudos como elemento decorativo de fondo | ⚠️ Adoptar con moderación — solo como textura muy sutil (opacidad <5%) en fondos, nunca como ilustración explícita |
| Iconografía de cuerdas/nudos literal | ❌ Evitar — cae directo en lo arqueológico/turístico que el brief pide evitar |
| Paleta de colores "andina" (colores vivos tipo textil) | ❌ Evitar — contradice la paleta fintech/SaaS elegida en 18.1 |

---

## 19. Diseño mobile

Mobile-first real, no "responsive de escritorio adaptado" — el material de proyecto ya lo exige para el dashboard (sección 12 del doc cargado) y debe aplicar a todo el sitio.

### 19.1 Estructura mobile

- **Header:** logo + menú hamburguesa + CTA primario visible siempre (sticky, no se pierde al hacer scroll).
- **Hero:** headline primero, visual del dashboard debajo (no al lado — en mobile el mockup pierde legibilidad si compite por ancho con el texto).
- **Secciones:** todas apiladas verticalmente, cards de "Para quién es" y "Servicios" en carrusel horizontal deslizable en vez de grid — evita scroll infinito.
- **Navegación del dashboard-vitrina:** replica el patrón ya definido en el material de proyecto: `Inicio | Impuestos | Documentos | Historial` como barra inferior fija, igual que el producto real la tendrá — coherencia entre lo que se promete y lo que se va a construir.

### 19.2 CTA en mobile

Botón primario "Quiero empezar" fijo en la parte inferior de la pantalla (sticky bottom bar) en todas las páginas de contenido — patrón estándar en apps fintech argentinas, y el que más sube conversión en mobile porque no depende de que el usuario haga scroll hasta encontrarlo.

### 19.3 Formularios en mobile

- Un campo por pantalla en el onboarding cuando el campo requiere teclado (nombre, CUIT, email) — reduce abandono.
- Los pasos de selección (tipo de contribuyente, situación actual) muestran las opciones como botones grandes tocables, nunca un `<select>` nativo escondido.

### 19.4 Pricing y dashboard preview en mobile

- Tabla de precios se convierte en cards apiladas, una por plan, con el plan recomendado (Mono Plus, si el volumen de mercado lo confirma) destacado con un borde de acento.
- Dashboard-vitrina en mobile muestra la versión real que tendría el producto (no una versión "resumida de la resumida") — es el momento de más impacto para demostrar que el producto es mobile-first de verdad.

---

## 20. SEO

### 20.1 Búsquedas objetivo y mapeo a páginas

| Búsqueda | Página que la captura | Title tag propuesto |
|---|---|---|
| contador Tucumán | `/` o `/sobre-kipux` | KIPUX — Estudio contable digital en Tucumán |
| estudio contable Tucumán | `/` | KIPUX — Estudio contable digital en Tucumán |
| contador monotributo Tucumán | `/servicios/monotributo` | Contador para Monotributo en Tucumán | KIPUX |
| monotributo Tucumán | `/servicios/monotributo` + artículos de `/recursos` | Monotributo en Tucumán: guía y gestión | KIPUX |
| contador online Tucumán | `/` | KIPUX — Contador online en Tucumán |
| estudio contable digital | `/` o `/sobre-kipux` | KIPUX — Estudio contable digital |
| contador para emprendedores | `/servicios` | Contador para emprendedores | KIPUX |
| contador para monotributistas | `/servicios/monotributo` | Contador para monotributistas | KIPUX |

### 20.2 Meta descriptions (ejemplo, home y página ancla)

- **Home:** "KIPUX es el estudio contable digital que automatiza tus vencimientos y te muestra tu situación fiscal en tiempo real, con respaldo de una contadora matriculada. Empezá en 3 minutos."
- **`/servicios/monotributo`:** "Gestión de monotributo con dashboard en tiempo real, alertas de vencimiento y respaldo de una contadora matriculada. Conocé los planes de KIPUX."

### 20.3 Jerarquía H1/H2 (regla general para todo el sitio)

- Un solo H1 por página, siempre alineado a la búsqueda objetivo de esa URL.
- H2 para cada sección funcional (ya detallados en las secciones 7, 9, 10, 11, 12, 14 de este documento).
- Nunca usar el H1 solo como eslogan de marca en páginas de servicio — el eslogan va de subheadline, el H1 lleva la intención de búsqueda.

### 20.4 URLs

Todas en minúscula, sin tildes, con guiones — ya reflejado en el sitemap (sección 5). Evitar parámetros de query para contenido indexable.

### 20.5 Estrategia de contenido (`/recursos`)

Categorías (alineadas a la sección 24 del brief):

1. **Monotributo** — categorías, recategorización, escalas anuales (el patrón "artículo ancla por año fiscal" que mejor ejecuta Countax, adoptado y mejorado con más conexión a producto).
2. **Ingresos Brutos** — específico Tucumán cuando aplique.
3. **Facturación** — factura C, factura E, errores comunes.
4. **Emprendedores** — primeros pasos, alta de actividad.
5. **Finanzas para pequeños negocios** — más orientado a fase 2 (visión de plataforma financiera).

**Regla editorial:** cada artículo cierra con un CTA contextual al servicio relacionado (no siempre "Quiero empezar" genérico) — es la falla que detecté en el contenido de Countax: mucho volumen, poca conexión con conversión.

### 20.6 Arquitectura para escalar más allá de Tucumán (regla 11 del brief)

El sitemap y el naming de URLs ya están armados sin "tucuman" hardcodeado en las rutas (excepto contenido editorial específico) — cuando KIPUX expanda a otra provincia, se agregan páginas de aterrizaje geográficas (`/tucuman`, `/salta`, etc.) sin reestructurar el sitio. Esto es una decisión de arquitectura tomada ahora para no pagar el costo de migración después.

---

## 21. Recomendación tecnológica

### 21.1 Comparación

| Criterio | WordPress | Webflow | Framer | Next.js (custom) |
|---|---|---|---|---|
| SEO | Bueno (con plugin) | Muy bueno, nativo | Muy bueno, nativo | Excelente, pero requiere implementarlo |
| Velocidad | Media (depende de hosting/plugins) | Buena | Muy buena | Excelente si está bien construido |
| Edición sin developer | Buena (a veces frágil con page builders) | Muy buena | Muy buena, orientada a diseño | Nula — cada cambio de copy requiere un deploy |
| Costo inicial | Bajo (hosting + tema) | Medio | Medio | Alto (desarrollo desde cero) |
| Integraciones (forms, WhatsApp, analytics) | Amplias vía plugins | Nativas + Zapier/Make | Nativas + Zapier/Make | Ilimitadas, pero cada una se construye |
| Animaciones/microinteracciones (khipu, sección 18.5) | Limitado sin código | Bueno | Excelente — es su punto fuerte | Ilimitado, pero cuesta tiempo de desarrollo |
| Escalabilidad a producto (dashboard futuro) | Baja — WordPress no es el lugar para un dashboard de cliente | Media — se integra por subdominio/API con una app aparte | Media — igual que Webflow | Alta — mismo stack que probablemente use el dashboard real |
| Curva de mantenimiento para Mariana sin developer | Media-alta (updates, seguridad, plugins) | Baja | Baja | Muy alta (siempre depende de un developer) |

### 21.2 Recomendación

**Para el MVP del sitio: Webflow.**

Justificación: el sitio necesita SEO fuerte desde el día uno (sección 20), edición de contenido sin depender de un developer para cada cambio de precio o FAQ, buena velocidad, y formularios/integraciones nativas para el flujo de onboarding (sección 13.2) sin construir backend propio. Framer es la alternativa más cercana — de hecho, si el peso relativo de la animación del motivo khipu (sección 18.5) termina siendo más importante que la escala del blog SEO, **Framer sería la segunda opción recomendada**, no una alternativa débil.

**Por qué no WordPress:** exige mantenimiento técnico continuo (seguridad, updates) que no aporta valor a un estudio contable digital que quiere verse como producto tecnológico — el riesgo de que "se vea a WordPress" (plugins genéricos, plantillas reconocibles) es alto si no hay presupuesto de diseño a medida.

**Por qué no Next.js para el sitio de marketing:** es la elección correcta para el dashboard funcional futuro (Fase 3), no para el sitio público del lanzamiento — cada cambio de copy o precio requeriría un deploy de developer, lo cual va directamente en contra de la velocidad de iteración que este proyecto necesita en sus primeros meses.

**Cómo se conecta con el futuro dashboard:** el sitio en Webflow vive en el dominio principal; el dashboard real (cuando se construya, probablemente en Next.js o similar — ver roadmap del material de proyecto, Fase 3) vive en un subdominio (`app.kipux.com.ar` o similar) con su propio login. No hay necesidad de migrar el sitio de marketing cuando eso pase.

---

## 22. Especificaciones para desarrollador

### 22.1 Páginas a construir (MVP)

Ver sitemap completo en sección 5. Total: 13 páginas indexables + páginas legales.

### 22.2 Componentes reutilizables

| Componente | Usado en |
|---|---|
| Header sticky con CTA | Todas las páginas |
| Footer | Todas las páginas |
| Card de plan de precio | Home, `/precios` |
| Card de perfil ("Para quién es") | Home |
| Dashboard-vitrina (mockup interactivo) | Home, `/dashboard`, hero |
| Acordeón de FAQ | Home (preview), `/preguntas-frecuentes` |
| Stepper de onboarding | `/empezar` |
| Banda de CTA final | Todas las páginas de contenido |
| Bloque de credencial profesional | Home, `/sobre-kipux` |

### 22.3 Comportamiento esperado

- CTA "Quiero empezar" siempre lleva a `/empezar`, nunca a un formulario genérico de contacto.
- El stepper de onboarding guarda progreso en el navegador (localStorage o equivalente) — si el usuario cierra la pestaña a mitad del paso 3, al volver no debería perder lo ya cargado.
- El dashboard-vitrina no debe requerir backend: es un componente con datos estáticos/mockeados, animado con CSS/JS del lado del cliente.

### 22.4 Responsive

Mobile-first (ver sección 19) con breakpoints estándar: mobile (<768px), tablet (768-1024px), desktop (>1024px). CTA sticky bottom bar solo en mobile/tablet.

### 22.5 Formularios

| Formulario | Campos | Destino de los datos |
|---|---|---|
| Onboarding (`/empezar`) | Ver sección 13.2 | `[COMPLETAR: CRM o email de destino — recomendado: integrar con HubSpot/Notion/planilla vía Zapier o Make desde el día 1, para no perder leads en un inbox]` |
| Contacto (`/contacto`) | Nombre, email, teléfono, mensaje | Igual que arriba |
| Newsletter/lead magnet (si se implementa un checklist descargable, ver sección 2) | Email | Herramienta de email marketing a definir |

### 22.6 Integraciones

- **WhatsApp Business API o link directo `wa.me`** — mínimo viable: link directo con mensaje prellenado.
- **Analytics:** Google Analytics 4 + Google Search Console desde el día 1 (indispensable dado el peso de la estrategia SEO, sección 20).
- **Meta Pixel** si se van a correr campañas pagas en Instagram (mencionado como canal en el material de proyecto).
- **Calendly o similar** — opcional, para quien prefiera agendar una llamada en vez de completar el onboarding (patrón adoptado de Contablix, sección 2).

### 22.7 Performance

- Imágenes optimizadas (WebP/AVIF), lazy loading fuera del viewport inicial.
- Animaciones del motivo khipu no deben bloquear el render inicial — cargar de forma diferida.
- Objetivo: Core Web Vitals en verde (LCP <2.5s, CLS <0.1) — impacta directo en el SEO objetivo de la sección 20.

### 22.8 Seguridad

- HTTPS obligatorio (estándar en Webflow/Framer).
- Formularios con protección anti-spam (reCAPTCHA o equivalente nativo de la plataforma).
- Ningún dato fiscal real del cliente pasa por el sitio de marketing — eso es exclusivo del futuro dashboard funcional, con su propia capa de seguridad a definir en esa etapa.

### 22.9 CMS y estructura de contenidos

- Blog/`Recursos`, FAQ y planes de precios deben ser colecciones editables por Mariana sin developer (CMS de Webflow o Framer) — no hardcodeados en el diseño.
- Estructura de colección "Recursos": título, slug, categoría, extracto, cuerpo, CTA contextual, fecha, imagen destacada.

### 22.10 Datos legales pendientes (a completar antes de publicar — no inventados en este documento)

- Razón social y CUIT de KIPUX.
- Matrícula profesional y Consejo Profesional correspondiente.
- Domicilio legal/comercial.
- Política de privacidad y tratamiento de datos personales (Ley 25.326) — redacción legal a cargo de asesoría correspondiente, no de este documento.
- Términos y condiciones del servicio.
- Disclaimer profesional (alcance del servicio, límites de responsabilidad).

### 22.11 Futuras integraciones (documentar, no construir en el MVP)

- Login de clientes → dashboard funcional real.
- Webhook/API de estado fiscal entre el motor de automatización (roadmap del material de proyecto) y el dashboard.
- Posible integración de pagos (cuando se defina si KIPUX cobra el abono directamente).

---

## 23. MVP vs Fase 2

| Se construye ahora (MVP del sitio) | Se deja preparado para después |
|---|---|
| Las 13 páginas del sitemap con copy completo | Login de clientes / dashboard funcional real |
| Dashboard-vitrina estático (mockup) | Dashboard con datos reales por cliente |
| Formulario de onboarding de 4 pasos (capta lead, no da de alta automáticamente) | Alta automática / integración directa con ARCA |
| Blog/Recursos con 3-5 artículos ancla iniciales | Estrategia de contenido a escala (calendario editorial extenso) |
| WhatsApp vía link directo | WhatsApp Business API con automatizaciones |
| Analytics básico (GA4 + Search Console) | Analytics de producto (comportamiento dentro del dashboard) |
| Precios con piso visible por plan | Cotizador dinámico tipo Contablix (si se valida que aporta conversión) |
| Testimonios: espacio preparado, vacío o con credencial profesional en su lugar | Testimonios reales de clientes (activar con 5-8 casos genuinos) |
| Páginas geográficas: solo Tucumán | Páginas de aterrizaje por provincia al expandir |

---

## 24. Checklist de lanzamiento

**Contenido y legal**
- [ ] Completar todos los `[COMPLETAR]` de este documento (matrícula, razón social, contacto, precios finales)
- [ ] Redactar Términos y Condiciones y Política de Privacidad con asesoría legal
- [ ] Confirmar alcance exacto de cada plan (qué incluye/excluye) con el equipo operativo

**Diseño y contenido**
- [ ] Aplicar identidad visual (sección 18) a las 13 páginas
- [ ] Producir el dashboard-vitrina (mockup interactivo, sección 15)
- [ ] Cargar copy final (revisado) de todas las páginas (secciones 7, 9-14)

**Técnico**
- [ ] Configurar dominio y hosting
- [ ] Conectar formularios a destino real (CRM/planilla/email)
- [ ] Instalar Analytics (GA4) y Search Console
- [ ] Verificar Core Web Vitals antes de publicar
- [ ] Probar el flujo de onboarding completo en mobile y desktop

**SEO**
- [ ] Title tags y meta descriptions de las 13 páginas (sección 20)
- [ ] Sitemap.xml y robots.txt
- [ ] 3-5 artículos ancla publicados en `/recursos` antes del lanzamiento

**Pre-lanzamiento**
- [ ] Revisión cruzada de todo el copy en tono rioplatense/argentino (sin neutro ni peninsular)
- [ ] Test de formularios end-to-end (que un lead de prueba llegue efectivamente a destino)
- [ ] Chequeo de que ningún dato fiscal ficticio del dashboard-vitrina se confunda con datos reales

---

## Cierre

Este documento cubre estrategia, arquitectura, copy completo y especificación funcional para que un diseñador y un desarrollador puedan trabajar sobre él directamente. Los puntos marcados `[COMPLETAR]` son las únicas piezas que faltan para que sea 100% accionable — todos son datos que solo vos podés confirmar (precios finales, matrícula, datos legales) o decisiones de producto que dependen de la validación de mercado que el material de proyecto ya identificaba como pendiente (unit economics, precio de mercado en Tucumán).

**Próximo paso recomendado:** cerrar los `[COMPLETAR]` de pricing y datos legales primero — son el bloqueante más rápido de resolver y el que más rápido desbloquea el resto (diseño, copy final, checklist de lanzamiento).

---

*Documento preparado como blueprint estratégico y funcional para el desarrollo del sitio web de KIPUX.*
*Mariana — KIPUX, San Miguel de Tucumán.*

