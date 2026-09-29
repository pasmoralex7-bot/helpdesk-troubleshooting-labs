# Lab 07 — Programa no inicia desde un acceso directo

**Tipo de práctica:** incidencia simulada en una máquina virtual con Windows 10 (VirtualBox).

## Ticket

**Usuario ficticio:** empleado administrativo.

**Problema reportado:** El usuario no podía iniciar un programa desde el acceso directo `Programa Laboratorio` ubicado en el escritorio. Al hacer doble clic, el programa no se iniciaba.

## Problema

Se reprodujo la incidencia haciendo doble clic en el acceso directo del escritorio. El programa no respondió como se esperaba.

## Diagnóstico

Se revisaron las propiedades del acceso directo para identificar qué ejecutaba Windows.

El acceso directo utilizaba `powershell.exe` y tenía configurado el siguiente archivo mediante el parámetro `-File`:

```text
C:\Users\Alex\Desktop\SoporteLab\ProgramaLaboratorio.ps1
```

Después se comprobó la carpeta `C:\Users\Alex\Desktop\SoporteLab` y se encontró que el archivo disponible era:

```text
ProgramaLaboratorio_v2.ps1
```

La comparación entre el destino configurado y el archivo existente permitió identificar la causa.

## Causa

El archivo había sido renombrado a `ProgramaLaboratorio_v2.ps1`, pero el acceso directo seguía haciendo referencia al nombre anterior `ProgramaLaboratorio.ps1`. Por este motivo, el destino configurado ya no correspondía con el archivo existente.

## Solución

Se modificó el campo **Destino** de las propiedades del acceso directo para que el parámetro `-File` apuntara a:

```text
C:\Users\Alex\Desktop\SoporteLab\ProgramaLaboratorio_v2.ps1
```

## Verificación

Se volvió a ejecutar `Programa Laboratorio` mediante doble clic desde el escritorio.

El programa inició correctamente y mostró el mensaje:

> Programa de laboratorio iniciado correctamente.

Esto confirmó que el acceso directo volvía a apuntar al archivo correcto y que la incidencia estaba resuelta.

## Aprendizaje

- Un programa puede seguir funcionando aunque falle el acceso directo utilizado para iniciarlo.
- Revisar el campo **Destino** permite comprobar qué archivo intenta ejecutar un acceso directo.
- Es importante comparar la ruta configurada con el archivo que realmente existe antes de modificar la configuración.
- La reparación debe verificarse repitiendo la misma acción que inicialmente producía el fallo.

## Herramientas utilizadas

- Windows 10
- Explorador de archivos
- Propiedades de accesos directos
- Windows PowerShell
