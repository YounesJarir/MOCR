# 💠 MFT Overlay Controlled Recovery (MOCR)

**Autor:** Younes Jarir  
**Licencia:** MIT  
**Versión:** 1.0 (public draft)

---

## 📘 Descripción general

**MOCR (MFT Overlay Controlled Recovery)** es una técnica de **recuperación forense para volúmenes NTFS dañados**, especialmente aquellos afectados por wipers o ransomware tipo *NotPetya*.

El método consiste en **inyectar una $MFT donante compatible** sobre un volumen parcialmente destruido para **restaurar su estructura lógica mínima** y **permitir el montaje parcial** del sistema de archivos.  
Esto mejora la efectividad de las herramientas de *carving* y recuperación posterior.

---

## ⚙️ Principio básico

1. **Identificación de variables base**  
   Extracción de los valores estructurales desde el VBR o sectores remanentes.

2. **Cálculo de coordenadas quirúrgicas**  
   Obtención de offsets precisos en bytes y sectores.

3. **Inyección controlada de la MFT donante**  
   Sustitución de la MFT dañada mediante alineación exacta.

4. **Montaje y verificación**  
   Validación del volumen y recuperación de datos.

---

## 🧩 Variables clave

| Variable | Descripción |
|-----------|-------------|
| `$PART_OFFSET_SECTORES` | Sector donde inicia la partición. |
| `$LCN_MFT` | Dirección lógica de la $MFT. |
| `$LCN_MFTMIRR` | Dirección lógica del $MFTMirr (copia espejo). |
| `$BYTES_PER_CLUSTER` | Tamaño de clúster NTFS. |
| `$PART_OFFSET_BYTES` | Offset de inicio de la partición en bytes. |
| `$OFFSET_MFT_CORRUPTA` | Offset exacto de la MFT dañada. |
| `$OFFSET_MFTMIRR_SANO` | Offset exacto del MFT espejo intacto. |
| `$SECTOR_OFFSET` | Offset expresado en sectores de 512 bytes. |

---

## ⚠️ Aviso legal

Este proyecto se distribuye bajo licencia **MIT**.  
Su finalidad es **educativa y de investigación forense**.  
El autor no se hace responsable del uso indebido de la técnica ni garantiza su eficacia en todos los entornos.

---

## 📅 Estado del proyecto

📄 Paper técnico en desarrollo.  
📦 Documentación y scripts próximamente.  
🧪 Pruebas realizadas en entornos VMware con volúmenes NTFS dañados.

---

© 2025 Younes Jarir — *MFT Overlay Controlled Recovery (MOCR)*
