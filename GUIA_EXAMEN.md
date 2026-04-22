# Guía del Examen - Auditoría de Sistemas (Banco)

## 1) Qué te están pidiendo exactamente

Debes entregar un proyecto funcional de auditoría de riesgos con:

1. Repositorio en GitHub con tu código mejorado.
2. Sistema ejecutando localmente (frontend + backend + modelo local).
3. Login ficticio (sin base de datos) funcionando.
4. Motor de IA mejorado y funcionando (no solo texto estático/mock).
5. Evaluación de 5 activos de información del entorno bancario.
6. Informe final completo en `README.md` y exportado a PDF.

---

## 2) Estado actual de tu proyecto (según revisión rápida)

1. Login ficticio: ya existe y está funcional.
2. Backend IA: existe en Flask con Ollama/OpenAI-compatible.
3. Frontend: actualmente genera riesgos/tratamientos con lógica mock en algunos flujos.
4. README: aún no está en formato final del entregable del examen.

Conclusión: ya tienes buena base. Te falta principalmente fortalecer evidencia de IA real + completar informe final con 5 activos.

---

## 3) Plan recomendado para asegurar nota máxima (20/20)

## Fase A - Repositorio y ejecución

1. Subir tu versión a GitHub (fork o repo propio).
2. Verificar ejecución local:
   - Frontend: `npm install` y `npm run dev`
   - Backend: `python app.py`
   - Modelo local: `ollama pull llama3:8b-instruct` (o el modelo que uses)
3. Documentar en README los comandos reales que sí usaste.

## Fase B - Login (5 pts)

1. Mantener login ficticio sin DB (usuario/clave hardcodeada o en archivo local).
2. Mostrar evidencia de:
   - Pantalla login.
   - Acceso exitoso.
   - Cierre de sesión.
3. Describir en 4-6 líneas cómo funciona (validación + token localStorage).

## Fase C - IA funcionando (5 pts)

1. Reemplazar mocks en frontend por consumo real a endpoints Flask:
   - `POST /analizar-riesgos`
   - `POST /sugerir-tratamiento`
2. Asegurar formato de salida consistente (riesgo, impacto, recomendación clara).
3. Manejar errores (timeout, modelo no disponible, respuesta incompleta).
4. Capturar evidencia de:
   - Código mejorado de IA.
   - Resultado real generado por IA en pantalla.

## Fase D - Evaluación de 5 activos (5 pts)

Elige 5 activos del anexo y para cada uno documenta:

1. Condición (hallazgo real o escenario plausible).
2. Recomendación alineada a ISO 27001.
3. Riesgo (probabilidad: Baja/Media/Alta).
4. Evidencia (captura de pantalla o salida de análisis).

## Fase E - Informe completo y PDF (5 pts)

1. Pegar estructura requerida en `README.md`.
2. Completar todos los campos (nombre, fecha, URL GitHub, evidencias, hallazgos).
3. Exportar README a PDF para aula virtual.

---

## 4) Las mejores opciones de herramientas (prácticas y defendibles)

Tu set actual:
- Docker
- Autopsy Digital Forensic
- CoolUtils Outlook Viewer
- FTK Imager
- RegRipper

Está bien para forense, pero para este examen te conviene combinarlo con herramientas de auditoría técnica y seguridad de aplicaciones.

## Opción recomendada por objetivo

1. Para levantar entorno y reproducibilidad
- Docker + Docker Compose.
- Ventaja: demuestras control del entorno y facilidad de réplica.

2. Para evaluación de servicios web (API, app web)
- Postman o Insomnia (pruebas de endpoints).
- OWASP ZAP (escaneo básico de vulnerabilidades web).
- curl para evidencia simple en consola.

3. Para análisis de infraestructura/red
- Nmap (descubrimiento de puertos/servicios).
- Wireshark (tráfico, evidencia de exposición/cifrado).

4. Para análisis de hardening/configuración
- Lynis (Linux) o CIS-CAT (si aplica).
- OpenSCAP (si tienes entorno Linux empresarial).

5. Para logs/correlación (si lo quieres elevar)
- Wazuh o ELK/SIEM básico para mostrar monitoreo.

6. Para LLM local en el examen
- Ollama + modelo instruct estable (`llama3:8b-instruct` o equivalente).
- Criterio: respuesta en español, rápida, repetible, sin depender de nube.

## Cómo encaja tu set actual

1. Autopsy/FTK Imager/RegRipper: útiles para evidencia forense (post-incidente), no para todo el flujo de auditoría de app.
2. CoolUtils Outlook Viewer: útil si auditas activo de correo electrónico ejecutivo.
3. Docker: sí es clave, mantenlo.

Recomendación final de stack mínimo ganador:
- Docker
- Postman
- OWASP ZAP
- Nmap
- Ollama
- (Opcional) Wireshark

---

## 5) 5 activos sugeridos (fáciles de justificar y con evidencia clara)

Para que el informe salga sólido, te conviene elegir activos auditables en laboratorio:

1. API Transacciones (Servicio Web)
- Hallazgo típico: falta de rate limiting o validación de entrada insuficiente.
- Riesgo: Alta.
- Recomendación ISO 27001: controles de seguridad en aplicaciones y pruebas periódicas.

2. Aplicación Web de Banca (Aplicación)
- Hallazgo típico: gestión de sesión débil o mensajes de error excesivos.
- Riesgo: Alta.
- Recomendación: endurecer autenticación, expiración de sesión, cabeceras seguras.

3. Servidor de Base de Datos (Base de Datos)
- Hallazgo típico: permisos sobredimensionados o cifrado en reposo no validado.
- Riesgo: Alta.
- Recomendación: mínimo privilegio, cifrado, backups probados.

4. Firewall Perimetral (Seguridad)
- Hallazgo típico: reglas permisivas, puertos abiertos no justificados.
- Riesgo: Media/Alta.
- Recomendación: revisión de reglas y segmentación de red.

5. Registros de Auditoría / Logs de Seguridad (Información)
- Hallazgo típico: retención insuficiente o logs no centralizados.
- Riesgo: Media.
- Recomendación: centralización SIEM, integridad y retención de logs.

---

## 6) Plantilla lista para pegar en README.md

> Reemplaza los campos entre corchetes y pega tus capturas.

```md
# Informe de Auditoría de Sistemas - Examen de la Unidad I

**Nombres y apellidos:** [Tu nombre]
**Fecha:** [dd/mm/aaaa]
**URL GitHub:** [https://github.com/tuusuario/turepo]

## 1. Proyecto de Auditoría de Riesgos

### Login
**Evidencia:**
[Captura del login]

**Descripción:**
Se implementó un inicio de sesión ficticio sin base de datos, validando credenciales predefinidas en el frontend y gestionando sesión mediante token local en localStorage.

### Motor de Inteligencia Artificial
**Evidencia:**
[Captura de la sección del código fuente mejorado de IA que permite su funcionamiento]

**Descripción:**
Se mejoró el motor de IA integrando llamadas reales al backend Flask con modelo local (Ollama), generando riesgos, impactos y recomendaciones de mitigación alineadas con ISO 27001.

## 2. Hallazgos

### Activo 1: API Transacciones
**Evidencia:** [Captura]
**Condición:** [Situación encontrada]
**Recomendación:** [Acción correctiva/preventiva]
**Riesgo:** Probabilidad [Baja/Media/Alta]

### Activo 2: Aplicación Web de Banca
**Evidencia:** [Captura]
**Condición:** [Situación encontrada]
**Recomendación:** [Acción correctiva/preventiva]
**Riesgo:** Probabilidad [Baja/Media/Alta]

### Activo 3: Servidor de Base de Datos
**Evidencia:** [Captura]
**Condición:** [Situación encontrada]
**Recomendación:** [Acción correctiva/preventiva]
**Riesgo:** Probabilidad [Baja/Media/Alta]

### Activo 4: Firewall Perimetral
**Evidencia:** [Captura]
**Condición:** [Situación encontrada]
**Recomendación:** [Acción correctiva/preventiva]
**Riesgo:** Probabilidad [Baja/Media/Alta]

### Activo 5: Registros de Auditoría
**Evidencia:** [Captura]
**Condición:** [Situación encontrada]
**Recomendación:** [Acción correctiva/preventiva]
**Riesgo:** Probabilidad [Baja/Media/Alta]
```

---

## 7) Checklist de entrega final

1. Login probado y con capturas.
2. IA real probada (sin mocks) y con capturas del código + salida.
3. Cinco activos completos con condición/recomendación/riesgo.
4. README completo con estructura oficial.
5. PDF exportado del informe.
6. Repositorio en GitHub actualizado y público/visible para revisión.

---

## 8) Consejo para defenderlo en clase

Cuando te pregunten, enfócate en este mensaje:

"El sistema usa IA local para proponer riesgos e impactos por activo, luego recomienda tratamientos de mitigación alineados a ISO 27001. El login es ficticio para control de acceso en entorno académico, y el informe consolida hallazgos priorizados por probabilidad de riesgo."