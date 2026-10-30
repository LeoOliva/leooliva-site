# Leonardo Oliva — sitio personal

Sitio estático bilingüe, sin dependencias de ejecución ni servicios externos. Incluye diseño adaptable, navegación móvil y preferencia de idioma guardada en el navegador.

## Configuración

Edita el objeto `contact` al inicio de `app.js` para actualizar correo y perfiles. Los enlaces iniciales provienen del diseño de Stitch; **verifícalos antes de publicar**, en particular Instagram, que apunta a la página general. Los textos se encuentran en `index.html` (inglés) y en el objeto `es` de `app.js` (español).

## Docker

```sh
docker build -t leonardo-site .
docker run --rm -p 8080:80 leonardo-site
```

Abre http://localhost:8080. El contenedor escucha en el puerto **80**.

## Dockploy

1. Sube este directorio a un repositorio Git y crea una aplicación en Dockploy desde ese repositorio.
2. Selecciona **Dockerfile** como método de construcción y usa `Dockerfile` en la raíz.
3. Configura el dominio y el puerto interno **80**, y despliega. No requiere variables de entorno ni base de datos.

Las rutas `/en` y `/es` seleccionan explícitamente el idioma. En `/` se usa la preferencia guardada o inglés por defecto. El servidor devuelve la página en ambas rutas; el navegador aplica la traducción. Por ello, los metadatos localizados se actualizan con JavaScript y los rastreadores que no ejecutan JavaScript verán los metadatos en inglés.
