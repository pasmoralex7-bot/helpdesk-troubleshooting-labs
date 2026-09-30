# Ticket 08 - Archivo en modo solo lectura

## Problema
El usuario reportó que no podía actualizar el archivo `Reporte-Semanal.txt`.

## Diagnóstico
Revisé las propiedades del archivo en busca de alguna configuración que pudiera impedir su modificación.

## Causa
El archivo tenía habilitado el atributo **Solo lectura**.

## Solución
Deshabilité la opción **Solo lectura** y apliqué los cambios.

## Verificación
Modifiqué el archivo, guardé los cambios y comprobé que se guardaron correctamente.

## Estado
**Resuelto**
