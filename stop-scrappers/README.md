# Spike - StopScraping

# ¿Qué son los Scrappers?

Esencialmente son programas encargados de extraer información desde un sitio web. Guardando esa información para ser procesada con diferentes fines.

## ¿Qué tipos de Scrappers existen?

- Arañas (Spiders), su objetivo es visitar un sitio web y seguir los links de manera recursiva para ir obteniendo datos, constan de una parte para obtener los recursos y un parseador html para obtener la información.

    El principal de ellos es el robot de Google. Asi que debemos tener cuidado con los bloqueos para no perder posicion en los Buscadores.

- ShellScripts, serian los mas básicos programas que usualmente usan curl o wget y buscan en el contenido usando grep. (Cosa bastante poco practica).
- Scrappers son aquellos basados en Jsoup o Scrappy (entre otros) se basan en patrones para extraer la informacion del HTML
- Screenscrapers, son los que se basan en Selenium o PhantomJS, usan un browser real, pueden ejecutar javascript, ajax, etc. Pueden obtener el texto desde el HTML incluso si los contenidos se cargan con posterioridad. Tambien tienen la posibilidad de hacer capturas de pantalla para procesar las imagenes con algun OCR aun que este proceso es menos usado por ser mas costoso.
- Servicios de scrapping como ScrapingHub o Kimono, son servicios especialistas en este trabajo, se encargan de tomar la información de una web y disponibilizarla para algun usuario. Son muy dificiles de detectar ya que utilizan casi todas las tecnicas disponibles.
- Uso de iframes, no necesariamente es un scraping como tal pero en algunos casos alguien puede hacer pasar información como si fuera de una web, cuando proviene de otra.
- Copy/Paste, contra esto es mucho mas dificil luchar, ya que son personas copiando y pegando el contenido en otro lado.

# ¿Cómo prevenirlo?

Existen varias técnicas, sin embargo todas ellas tienen alternativas para ser evadidas, pero el evadirlas conlleva un trabajo extra, que no necesariamente es asumido por las personas que realizan esta actividad.

## RateLimit

Los usuarios normalmente hacen pocas peticiones por segundo, un Scrapper hace muchas, entonces se puede detectar en ese sentido y bloquear las peticiones.

Aun que un Scrapper también puede disminuir su velocidad, lo hace poco efectivo.

## Bloqueo de IP

Se puede bloquear una IP para no acceder a alguna página o servicio, pero el uso de Proxy y VPN, son de uso un comun para Scrappers. 

Si puede aplicarse para Scrappers que corren en servicios Cloud (AWS, GoogleApp, etc)

## Verificar el UserAgent

Un error comun que se puede aprovechar es que muchos Scrapper no agregan el UserAgent a las cabeceras de sus peticiones, entonces si no se informa de seguro no es un usuario.

También puede ser util mantener una BlackList de UserAgents, dado que aveces el programador del Scrapper no lo cambia y usa los que vienen por defecto o usa algo muy básico, por ej: "Mozilla" y solo eso.

Así también si detectas otros Scrappers los agregas a la BlackList

## Captcha

Un captcha por lo general hace preguntas al usuario en base a alguna imágen, así verifica que sea humano y no un script.

Alternativamente tambien existen software anticaptcha, que realiza reconocimiento de imagenes, pero son mas costosos y probablemente mas lentos de implementar.

Se puede usar en combinacion con otras tecnicas para bloquear Scrappers

Se sugiere usar un servicio relativamente inteligente para los captcha así no molestar tanto al usuario. Aun que de igualmanera sera una molestia.

## Login y Registro

Requerir la creación de cuenta y realizar login en el sitio puede ser una tecnica util.

Sin embargo los Scrappers pueden pasar atravez de este proceso incluso usando cuentas de correo temporales.

## Evita dar pistas

Debes evitar dar pistas de por que se realiza el bloqueo, por ejemplo si bloqueas por:

- RateLimit normalmente indicas como respuesta: Too many request
- Peticiones sin UserAgent: Error User Agent Missing.

En lugar de eso mejor decir: InternalError o algun otro error y pedir que se contacten con  soporte.

## Info como imágen

Podria ser util mostrar la información como una imagen. Ya que no es copiable directamente.

Sin embargo estas imagenes tambien podrian ser procesadas por OCR. Aun que es un proceso mas lento y costoso.

## Ofuscar endpoints

A nivel Javascript se debe asegurar el ofuscar los endpoints para hacer dificil la utilización de terceros.

No es infalible claramente, pero lo hace mas dificil.

## Cambiar html

Al cambiar frecuentemente el HTML las instrucciones del programa Scrapper dejan de funcionar, si los cambios de HTML son manuales normalmente esos casos son corregidos y se pone en marcha el Scrapper nuevamente. Si los cambios son por Framework, son mas dificiles de seguir. Pero tambien el software en cuestion es mas dificil de manejar y testear. Y nunca son infalibles, aun que el HTML se genere dinamicamente el Scrapper buscará patrones de texto para sacar la información dejando de lado posiciones xpath o ids o css.

## Honeypot (trampillas)

Con la finalidad de detectar Scrappers se puede generar algun link para generar bloqueos automaticos.

```coffeescript
<div class="result" style="display:none">
	<h3>blablabla</h3>
	Mas info <a class="link" href="/atrapa-scrapper">aquí</a>.
</div>
```

Este texto al tener un `display:none` no se muestra al usuario, pero un Scrapper podria intentar seguir el link y autobloquearse al realizar el request.

Se evade al programar en el Scrapper que ignore el contenido de este tipo de bloque o el `visibility:hidden` .

Considerar modificar robots.txt para evitar que los Buscadores se bloqueen.

## FakeInfo

Si detectas un Scrapper podrias generar información falsa solo para él. Haciendo bastante dificil que el Scrapper pueda detectar que la información entregada no sirve.

## Verificar el referer

Similar a la verificación de User Agent, pero tampoco es dificil de simular por parte del Scrapper.

Ojo: aveces los browsers pudieran no enviar el referer.

## Ofuscar la data

En el caso de las APIs tambien se puede ofuscar la data entregada. Incluso pensar en encodear o encriptar luego en el cliente procesa las respuestas.

## Abrir tus datos

Esta última tambien puede ser una opción: hacer tus datos públicos, asi consigues la autoria de la información con lo que ya no se hace necesario que te Scrapeen!

Te haces mas buscable, y la gente te podria agradecer el compartir la info.



# Referencias

[5 Tips For Web Scraping Without Getting Blocked or Blacklisted - Scraper Api](https://www.scraperapi.com/blog/5-tips-for-web-scraping/)

[How do I prevent site scraping?](https://stackoverflow.com/questions/3161548/how-do-i-prevent-site-scraping)
