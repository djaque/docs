# Spike - StopScraping

# Â¿QÃ© son los Scrappers?

Esencialmente son programas encargados de extraer información desde un sitio web. Guardando esa información para ser procesada con diferentes fines.

## Â¿Que tipos de Scrappers existen?

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

[Técnicas](Spike%20-%20StopScraping%20d8446385db8e42b382fb155bc09678d7/Te%CC%81cnicas%20c399f5a70e9c4e459ad193f29a5e398c.csv)

Referencias

[5 Tips For Web Scraping Without Getting Blocked or Blacklisted - Scraper Api](https://www.scraperapi.com/blog/5-tips-for-web-scraping/)

[How do I prevent site scraping?](https://stackoverflow.com/questions/3161548/how-do-i-prevent-site-scraping)
