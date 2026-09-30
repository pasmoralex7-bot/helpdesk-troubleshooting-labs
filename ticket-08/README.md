# Ticket 08 - Ruta incorrecta en acceso directo a recurso compartido

## Problema
El usuario reportó que no podía acceder a la carpeta `Documentos Empresa` mediante el acceso directo del escritorio.

## Diagnóstico
Intenté acceder mediante el acceso directo y Windows indicó que no podía encontrar el recurso. Utilicé `net share` para comprobar los recursos compartidos disponibles y detecté que el nombre del recurso no coincidía con la ruta utilizada por el acceso directo.

## Causa
La ruta configurada en el acceso directo era incorrecta y apuntaba a un recurso compartido inexistente.

## Solución
Modifiqué la ruta en las propiedades del acceso directo para que apuntara al recurso compartido correcto.

## Verificación
Volví a abrir el acceso directo y comprobé que se podía acceder correctamente a la carpeta y a sus archivos.

## Evidencia
La evidencia muestra que el acceso directo estaba configurado con la ruta incorrecta `\\localhost\DocumentosArchivo`.

![Ruta incorrecta configurada en el acceso directo](Evidencias/01-ruta-incorrecta-acceso-directo.png)

## Estado
**Resuelto**

---

*Ticket documentado y verificado en laboratorio.*
