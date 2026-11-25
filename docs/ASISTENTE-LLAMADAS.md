# Asistente de llamadas por liga (Mi Liga GPT)

## Qué es
Cada liga que usa la aplicación tiene un asistente de voz para llamadas de
información. En la página web de la liga aparece un botón **«Llamar»** (y, si la
liga contrata número, el número). Quien llama pregunta y el asistente responde
con la información registrada en la aplicación de ESA liga.

## Dos formas

### A. Llamada por internet — costo $0 (la forma principal)
- Botón **«Llamar»** en la página pública de la liga (`#/p/<liga>`).
- La llamada es por el navegador (voz del teléfono): la persona habla desde su
  celular o computadora, sin marcar ningún número y sin pagar minutos.
- La voz usa el reconocimiento y la síntesis del propio navegador/teléfono
  (gratis, viene en Chrome/Android); no se paga nada por la voz.
- El asistente que contesta es el motor local que ya tiene la app
  (`app/chatbot.js`): responde con los datos PÚBLICOS de la liga. No inventa:
  si no tiene el dato, lo dice.
- Por liga: el asistente solo ve los datos de esa liga; cada liga tiene su
  propio botón y su propio asistente.
- Sin servidor nuevo: el motor local corre en el dispositivo; el tope diario
  `chat_take` ya existe en la base.

### B. Número de teléfono real — opcional, con costo
- Un número mexicano por liga, vía Twilio u otro operador. Referencia
  (nov 2026, verificar al contratar): número local ~$6.25 USD/mes
  (~$132 MXN/mes); llamada entrante ~$0.01 USD/min (~$0.21 MXN/min);
  número móvil ~$15 USD/mes.
- El número recibe la llamada y el audio pasa por el mismo motor
  (voz a texto → motor local → texto a voz).
- La liga decide si lo contrata; no es parte del producto base.
- Por WhatsApp NO se puede: WhatsApp no deja que un bot conteste llamadas
  de voz.

## Qué responde y qué NUNCA responde
- Sí: tabla, próximos partidos, últimos resultados, goleadores, horarios,
  cancha, cómo inscribirse, cuotas públicas (si la liga las publica).
- Nunca: datos de jugadores (fotos, documentos, teléfonos, correos),
  finanzas, sanciones, ni nada privado. Igual que el asistente de chat:
  solo datos públicos.

## Estado
Especificación registrada 2026-11-25. No implementado. Implementar el modo A
cuando George lo autorice (Trabajo 3 en `prompt-mi-liga-gpt.txt`).
