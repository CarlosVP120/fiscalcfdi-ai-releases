# FiscalCFDI AI — descargas

Instaladores de FiscalCFDI AI para Mac (Apple Silicon e Intel) y Windows. Las descargas son públicas para que el canal de actualización funcione sin iniciar sesión en GitHub. No se incluyen claves de OpenRouter, datos contables ni perfiles de desarrollo. El código está en CarlosVP120/deepseek-harness.

## Instalación

Descarga el instalador de tu equipo desde Releases. En Mac, abre el DMG y copia FiscalCFDI AI a Aplicaciones. Si macOS bloquea la primera apertura por no estar notarizada, usa Ajustes del Sistema → Privacidad y seguridad → Abrir igualmente. En Windows, ejecuta el instalador; puede aparecer un aviso de editor desconocido.

Configura tu clave en Ajustes → Modelos → OpenRouter. El motor contable (CONTPAQi) se instala aparte; la app lo encuentra mediante `~/.fiscalcfdi-ai/engine.json`. En Mac, permite el acceso a la carpeta donde viva el motor cuando macOS lo pida.

La aplicación consulta el canal de actualización de este repositorio y presenta las actualizaciones disponibles; también puedes instalar una versión nueva manualmente desde Releases. No incorpora ningún token de GitHub.

## Publicar una actualización

En Actions → Instaladores internos → Run workflow, introduce el commit validado del fork (40 caracteres), la versión común (por ejemplo `0.2.1-alpha.1.20261016.1`), activa `enable_updates` y elige win-x64, mac-arm64 o mac-x64. Repite para los tres destinos.

Cuando las tres compilaciones pasen, publica una Release normal (no prerelease) con versión mayor que la instalada. Incluye los instaladores, los ZIP de Mac, los blockmaps y los metadatos `nightly.yml` y `nightly-mac.yml`; combina en este último las entradas ZIP de ambas arquitecturas sin cambiar nombres, tamaños ni SHA-512. El canal usa `releases/latest/download`, así que la Release debe ser la última publicación normal.

Mac se firma con el certificado autofirmado «FiscalCFDI AI Self-Signed», guardado como secretos de este repositorio (`MAC_CS_P12_BASE64`, `MAC_CS_P12_PASSWORD`) e importado en un llavero temporal del corredor. Conserva el mismo certificado entre versiones para que las actualizaciones se instalen y macOS conserve los permisos de la app. No es notarización de Apple.
