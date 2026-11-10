# Sesión 14 — Builds firmados

## Alcance congelado

El paquete Android mantiene el identificador `pe.edu.upeu.pharmamobile`, `versionCode = 1` y `versionName = 1.0.0`. La variante Release activa R8/minificación y usa las reglas de ProGuard del proyecto. La clave de firma se mantiene fuera de Git; el archivo local `keystore.properties` y cualquier JKS/keystore quedan excluidos por `.gitignore`. Existe `keystore.properties.example` sin credenciales.

Esta copia no incluye el almacén de firma del proyecto original ni su `keystore.properties`. Para distribuir una versión de Gabriel Vasquez Toro, crea un keystore nuevo fuera del proyecto y configura una ruta privada en el archivo ignorado `keystore.properties`. Respalda de forma segura el nuevo JKS y sus credenciales; no publiques ninguno de esos elementos.

## Builds y verificación

Los comandos de entrega son:

```powershell
./gradlew.bat :androidApp:bundleRelease :androidApp:assembleRelease
```

Los APK/AAB del proyecto original se excluyeron porque están firmados con el certificado de otra persona. Después de configurar una clave propia, genera los builds y verifica el certificado con `apksigner verify --verbose --print-certs`. El AAB se usa para distribución por Google Play; el APK sirve para instalación de revisión.

## iOS y matriz física

Una compilación/archive firmado de iOS y un IPA requieren macOS, Xcode, certificados Apple y perfil de aprovisionamiento válidos. El entorno de trabajo es Windows, por lo que no se ha generado ni firmado un IPA. Tampoco se atribuyen pruebas a teléfonos físicos sin dispositivos conectados. Registrar fabricante/modelo/versión, build instalada, flujos ejecutados, resultado y defectos observados en `docs/MATRIZ_PRUEBAS_DISPOSITIVOS.md` al completar esa validación.

## Instalación y checklist

Consulta `docs/GUIA_INSTALACION_Y_CHECKLIST.md` para generar/instalar el APK, verificar la firma y preparar la validación. El tag de versión final de esta copia debe crearse después de revisar los artefactos propios de Gabriel y completar las pruebas de entrega documentadas.
