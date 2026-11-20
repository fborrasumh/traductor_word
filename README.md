# TraducIA

Traduce documentos Word (.docx) a otro idioma y devuelve un .docx con el mismo diseño. La IA traduce párrafo a párrafo y el código comprueba cada traducción. Es una aplicación web de un solo fichero. Antes se llamaba *Traductor Word* (*WordTranslator Pro*, v1).

**Usar la app:** https://fborrasumh.github.io/traductor_word/

**Idiomas de la interfaz:** español (por defecto), inglés y portugués; selector en la barra superior (o `?lang=en` / `?lang=pt` en la URL).

## Qué hace

- Lee uno o varios .docx en el navegador, sin librerías externas, y traduce el cuerpo, las notas al pie y al final y, si se quiere, las cabeceras y los pies de página.
- Origen detectado automáticamente o elegido; destino: español, inglés (Reino Unido o EE. UU.), portugués (Portugal o Brasil), catalán, euskera, gallego, francés, italiano y alemán.
- Conserva estilos, tablas, imágenes, numeración, cabeceras, pies, notas al pie, campos (citas de Zotero o Mendeley, número de página), marcadores y cambios controlados: solo se sustituye el texto de cada párrafo.
- Conserva el **formato dentro del párrafo** (negritas, cursivas, enlaces, inserciones controladas): cada tramo con formato propio viaja como `⟦n⟧…⟦/n⟧` y cada elemento fijo (tabulación, imagen, nota, cita) como `⟦n/⟧`. El código vuelve a colocarlos aunque la traducción cambie el orden de las palabras.
- Glosario obligatorio, indicaciones para la IA (área, registro, variante), segunda pasada de revisión opcional y modo prueba (10 párrafos por documento).
- Estimación previa de peticiones y tokens; con los precios que escribe la persona, coste estimado y límite de gasto.
- Guarda cada lote traducido en el navegador en cuanto llega: si se corta, se sigue donde se dejó.
- Revisión párrafo a párrafo: reintentar con la IA, editar a mano o aceptar. Descarga del .docx, de todos en ZIP y de un informe CSV con todas las comprobaciones.
- Cambia el idioma de corrección ortográfica de Word al de destino (opcional).
- Un ejemplo que funciona sin clave, en cada idioma de la interfaz, con tres errores que el código detecta.

## La IA propone, el código comprueba

En cada párrafo traducido, el código comprueba:

| Comprobación | Qué detecta |
|---|---|
| Marcas de formato | Marcas perdidas, inventadas, anidadas o mal cerradas |
| Datos protegidos | Que vuelvan todas las URL, correos, teléfonos y DNI/NIE |
| Cifras | Cifras del original que faltan y cifras nuevas (admite el cambio de separador decimal) |
| Glosario | Términos del glosario presentes en el original cuya traducción obligatoria no aparece |
| Longitud | Traducciones mucho más cortas o largas que el original (posible omisión o añadido) |
| Respuesta | Párrafos que la IA no devolvió |

Si algo falla, se reintenta una vez describiendo el problema a la IA; el reintento solo se acepta si mejora. Lo que siga mal queda marcado para que la persona decida. Si las marcas de formato no cuadran, el párrafo se coloca sin formato interno y se avisa. La segunda pasada de revisión tampoco se acepta si empeora las comprobaciones.

## Cómo se usa la IA

Con la propia clave de OpenAI, Google Gemini o Anthropic Claude, y el modelo que elija cada persona (se listan los modelos de su clave). La clave se guarda solo en el navegador. No hace falta servidor.

## Privacidad

- Los documentos, el glosario y las traducciones se guardan solo en el navegador (IndexedDB). «Quitar» los borra.
- Hacia el proveedor de IA sale el texto de cada párrafo, con marcas en lugar del formato. Las URL, correos, teléfonos y DNI/NIE **no salen**: viajan como `⟦M1⟧`, `⟦M2⟧`… y se restauran en el navegador.
- Los nombres de personas y el resto del texto sí salen: no traduzcas documentos que no puedas compartir con tu proveedor.
- Antes del primer envío de la sesión se muestra una muestra de lo que sale y se pide confirmación.

## Límites

- No traduce gráficos, SmartArt, ecuaciones, texto dentro de imágenes, comentarios ni el contenido de los campos (citas, índices). Si hay índice, hay que actualizarlo en Word.
- Los cuadros de texto se traducen en su versión moderna; la copia de compatibilidad para versiones antiguas de Word (`mc:Fallback`) queda en el idioma original.
- Dentro de un enlace o de un control de contenido con varios formatos, el texto traducido toma el formato del primer tramo.
- No abre .doc antiguos ni documentos con contraseña.
- Las comprobaciones detectan pérdidas y cambios, no la calidad de la traducción: hay que revisarla. La estimación de coste es aproximada (unos 3,5 caracteres por token).
- Probada con IA simulada (incluidos errores provocados) y con documentos de prueba abiertos en LibreOffice y python-docx; no con todas las variantes de Word.

## Autoría

Fernando Borrás Rocher (Universidad Miguel Hernández de Elche). ORCID: [0000-0002-5519-4573](https://orcid.org/0000-0002-5519-4573)

## Cómo citar

Borrás Rocher, F. (2026). *TraducIA (Traductor Word)* (v2.0.0) [Software]. Zenodo. https://doi.org/10.5281/zenodo.21423391

## Licencia

MIT. Véase [LICENSE](LICENSE).
