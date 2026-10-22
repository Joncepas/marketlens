# MarketLens — prototipo PWA

MarketLens es un prototipo de aplicación web instalable para análisis personal de acciones, ETF, sectores y criptoactivos.

## Funciones actuales
- Lista de seguimiento guardada localmente en el navegador.
- Registro de precio, valor razonable estimado, crecimiento esperado, riesgo financiero, calidad, ventaja competitiva, fuente y tesis.
- Cálculo del margen de seguridad y puntuación heurística explicable.
- Exportación de los análisis a JSON.
- Interfaz adaptable a móvil y soporte PWA/service worker.

## Limitaciones importantes
- No obtiene precios ni fundamentales automáticamente.
- El valor razonable es manual: no hay un modelo DCF automático en esta primera versión.
- No es asesoramiento financiero y no genera órdenes de compra/venta.
- Los datos permanecen en el navegador del dispositivo; exporta una copia de seguridad.
- El service worker permite conservar la interfaz para uso offline después de la primera carga, pero no convierte datos ausentes en datos actuales.

## Cómo probarla
1. Descomprime el ZIP.
2. Para probar localmente, sirve la carpeta con un servidor HTTP local (por ejemplo, `python -m http.server 8000`) y abre `http://localhost:8000`.
3. Para instalarla como PWA, publícala en un hosting estático con HTTPS. Los planes gratuitos de algunos hostings pueden servir, pero sus condiciones pueden cambiar.
4. En Android/Chrome, abre la web y usa “Instalar app” o el menú “Añadir a pantalla de inicio”. En iPhone/Safari, usa Compartir → Añadir a pantalla de inicio.

## Siguiente fase recomendada
Integrar fuentes de datos fiables por medio de una capa de proveedores, con timestamp, moneda, cobertura, atribución y manejo explícito de límites de API. Mantener claves API fuera del código cliente si el proveedor requiere secreto; en ese caso hará falta un backend o función serverless y comprobar los límites gratuitos del alojamiento.

## Fuentes para consultar manualmente
- SEC EDGAR: https://www.sec.gov/edgar/search/
- AnnualReports: https://www.annualreports.com/
- iShares: https://www.ishares.com/
- justETF: https://www.justetf.com/
- CoinGecko: https://www.coingecko.com/
- FRED: https://fred.stlouisfed.org/

## Fórmulas
Margen de seguridad = (valor razonable − precio actual) / valor razonable.

La puntuación de 0–100 combina de forma heurística margen de seguridad, calidad, ventaja competitiva, riesgo financiero y crecimiento. No es una probabilidad, no está calibrada históricamente y no debe compararse sin más entre clases de activos.


## Publicación gratuita recomendada (GitHub Pages)
1. Crea una cuenta en GitHub si aún no tienes una.
2. Crea un repositorio público llamado `marketlens`.
3. Descomprime el ZIP y sube los archivos que están dentro de `MarketLens_PWA_v1/` a la raíz del repositorio (no subas el ZIP como único archivo).
4. En el repositorio, abre **Settings → Pages**.
5. En “Build and deployment”, elige **Deploy from a branch**, selecciona `main` y `/ (root)`, y guarda.
6. Espera a que GitHub publique la web. La URL será similar a `https://TU-USUARIO.github.io/marketlens/`.
7. Abre esa URL en tu móvil. Android/Chrome: menú ⋮ → Instalar app/Añadir a pantalla de inicio. iPhone/Safari: Compartir → Añadir a pantalla de inicio.

La publicación pública hace que la interfaz sea accesible en Internet. Los análisis guardados siguen en el almacenamiento local de cada navegador, no se sincronizan entre dispositivos.
