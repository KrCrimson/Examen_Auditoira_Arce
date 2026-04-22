# Guía Rápida de Comandos para Tomar Capturas

Objetivo: ejecutar el proyecto, generar evidencia y pegar capturas en el informe del README.

## 1) Comandos de preparación (PowerShell)

Abrir PowerShell en la carpeta del proyecto y ejecutar:

1. cd c:\Users\EPIS\Documents\Git\Auditoria_Arce\AuditoriaRiesgos
2. npm install
3. pip install flask openai
4. ollama pull llama3:8b-instruct

Si ya tienes dependencias instaladas, puedes omitir npm install y pip install.

## 2) Levantar servicios en 3 terminales

Terminal A (modelo local):
1. ollama serve

Terminal B (backend Flask):
1. cd c:\Users\EPIS\Documents\Git\Auditoria_Arce\AuditoriaRiesgos
2. python app.py

Terminal C (frontend Vite):
1. cd c:\Users\EPIS\Documents\Git\Auditoria_Arce\AuditoriaRiesgos
2. npm run dev

Abrir en navegador:
- http://localhost:5173

## 3) Credenciales de login para evidencia

- Usuario: admin
- Contraseña: 123456

## 4) Lista exacta de capturas que debes tomar

1. Captura Login:
- Pantalla en http://localhost:5173 mostrando formulario antes de iniciar sesión.
- Pegar en sección Login > Evidencia del README.

2. Captura Sesión iniciada:
- Pantalla principal del sistema con usuario autenticado en el encabezado.
- Puedes usarla como evidencia complementaria del login.

3. Captura Código de login:
- Abrir archivo src/components/Login.jsx y tomar captura del bloque principal del formulario.
- Abrir archivo src/services/LoginService.js y tomar captura de validación mock.

4. Captura Código de IA:
- Abrir archivo app.py y capturar funciones de endpoints y funciones:
  - analizar_riesgos
  - sugerir_tratamiento
  - obtener_riesgos
  - obtener_tratamiento
- Pegar en sección Motor de Inteligencia Artificial > Evidencia.

5. Captura Resultado IA (riesgos/tratamiento):
- En la app, agrega un activo y ejecuta recomendación.
- Toma captura de la tabla con activo, riesgo, impacto y tratamiento.

6. Capturas de Hallazgos (5 activos):
- Una captura por activo evaluado.
- Puede ser salida de la app, evidencia de endpoint o pantalla de análisis.

## 5) Activos sugeridos para llenar el informe

Usa estos 5 activos para mantener consistencia con el README:
1. API Transacciones
2. Aplicación Web de Banca
3. Servidor de Base de Datos
4. Firewall Perimetral
5. Registros de Auditoría

## 6) Comandos opcionales para prueba de endpoints (evidencia técnica)

Puedes usar estos comandos en PowerShell para demostrar backend:

1. Invoke-RestMethod -Method Post -Uri http://localhost:5500/analizar-riesgos -ContentType application/json -Body '{"activo":"API Transacciones"}'
2. Invoke-RestMethod -Method Post -Uri http://localhost:5500/sugerir-tratamiento -ContentType application/json -Body '{"activo":"API Transacciones","riesgo":"Acceso no autorizado","impacto":"Exposición de datos"}'

Toma captura de la salida en terminal y úsala como evidencia adicional.

## 7) Exportar el informe a PDF

Opción simple en VS Code:
1. Abrir README.md
2. Abrir vista previa Markdown
3. Imprimir o exportar como PDF

Opción navegador:
1. Subir README a GitHub
2. Abrir README renderizado
3. Imprimir del navegador y guardar como PDF

## 8) Cierre de procesos al terminar (PowerShell)

1. taskkill /F /IM node.exe
2. taskkill /F /IM python.exe
3. taskkill /F /IM ollama.exe

Con esto quedas listo para: ejecutar, capturar, pegar evidencias y exportar PDF.