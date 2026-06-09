# coding-project-template

# Ejecutar las aplicaciones

## Ejecutar el backend

En la terminal estándar `theia@theiadocker` (no en la de MySQL CLI), ejecuta el siguiente comando para iniciar la aplicación backend:

```bash
cd /home/project/java-database-final/back-end && mvn spring-boot:run
```

Si la aplicación sigue ejecutándose desde un proceso anterior, presiona **Ctrl+C** para detenerla y vuelve a ejecutar el comando.

Esto debería iniciar la aplicación de Spring Boot en el puerto **8080**.

### Si el puerto 8080 ya está en uso

Ejecuta el siguiente comando para finalizar el proceso que ocupa el puerto:

```bash
fuser -k 8080/tcp
```

Luego vuelve a iniciar el backend:

```bash
cd /home/project/java-database-final/back-end && mvn spring-boot:run
```

---

## Iniciar el backend y copiar la URL

Usa la función **Launch Application** del entorno de laboratorio.

1. Ingresa `8080` como puerto.
2. Haz clic en el ícono **Open in new browser tab**.
3. Verás un error, lo cual es normal.
4. Copia la URL completa que se abre en el navegador.

Necesitarás esta URL para conectar el frontend con el backend.

---

## Configurar el frontend

### Actualizar script.js

Abre el archivo `script.js` y establece `apiURL` con la URL del backend copiada anteriormente.

**No incluyas la barra final `/`.**

Ejemplo:

```javascript
const apiURL = 'https://captainfedo1-8080.theiadockernext-0-labs-prod-theiak8s-4-tor01.proxy.cognitiveclass.ai';
```

> Tu URL será diferente.

---

### Actualizar reviews.html

Abre `reviews.html` y modifica la URL dentro de la función `getReviews(storeId, productId)` usando la misma URL base del backend.

Reemplaza:

```javascript
url = `URL/reviews/${storeId}/${productId}`;
```

Por algo similar a:

```javascript
function getReviews(storeId, productId) {
    url = `https://captainfedo1-8080.theiadockernext-0-labs-prod-theiak8s-4-tor01.proxy.cognitiveclass.ai/reviews/${storeId}/${productId}`;
    
    fetch(url, {
        method: "GET",
        headers: {
            "content-type": "application/json"
        }
    });
}
```

> Tu URL será diferente.

---

## Ejecutar el frontend

En la terminal ejecuta:

```bash
cd /home/project/java-database-final/front-end && python3 -m http.server
```

Esto iniciará un servidor HTTP de Python y servirá el frontend en el puerto **8000**.