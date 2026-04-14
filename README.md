# F_Record 3 — Instalación en Photoshop 2020

## Requisitos

- Adobe Photoshop 2020 (versión 21.x)
- Windows 10/11

---

## Paso 1 — Copiar la extensión

Copia la carpeta `com.f_know.f_record.cep` a la siguiente ruta:

```
C:\Users\<tu_usuario>\AppData\Roaming\Adobe\CEP\extensions\
```

> Si la carpeta `extensions` no existe, créala manualmente.

---

## Paso 2 — Activar modo desarrollador (evitar error de firma)

Adobe requiere que las extensiones estén firmadas digitalmente. Para omitir esa verificación, ejecuta los siguientes comandos en **PowerShell como administrador**:

```powershell
reg add "HKCU\Software\Adobe\CSXS.10" /v PlayerDebugMode /t REG_SZ /d 1 /f
reg add "HKCU\Software\Adobe\CSXS.9" /v PlayerDebugMode /t REG_SZ /d 1 /f
```

### Alternativa manual (regedit)

1. Abre `regedit` (Win + R → escribe `regedit`)
2. Navega a: `HKEY_CURRENT_USER\Software\Adobe\CSXS.10`
   - Si la clave no existe, créala
3. Crea un valor de tipo **String** con nombre `PlayerDebugMode` y valor `1`
4. Repite lo mismo en `HKEY_CURRENT_USER\Software\Adobe\CSXS.9`

---

## Paso 3 — Abrir Photoshop

Cierra y vuelve a abrir Photoshop 2020. La extensión aparecerá en:

**Ventana → Extensiones → F_Record 3**

---

## Notas

- El modo desarrollador solo afecta a tu usuario de Windows, no al sistema.
- Photoshop 2020 usa CEP versión 10 (por eso se modifican las claves `CSXS.10` y `CSXS.9`).
