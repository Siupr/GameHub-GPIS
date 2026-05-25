1: USUARIOS WP:
Administrador
Nombre: admin_gamehub
Contraseña: admingamehub_123321
Correo: carlos.coves05@gmail.com
Editor (Redactor):
Nombre: redactor
Contraseña: redactor123
Correo: siupr71@gmail.com
Colaborador:
Nombte: colaborador
Contraseña: colaboraor123
Correo: garse71@gmail.com
Suscriptor:
Nombre: suscriptor
Contraseña :sub123
Correo: francisco.carbonell02@goumh.umh.es


2:  GUÍA INSTALACIÓN


Este manual describe, paso a paso, cómo instalar y poner en marcha la plataforma **GameHub** en un equipo local con Windows. El sistema está construido sobre **WordPress** con un tema hijo propio (`gamehub-child`) y una base de datos **MySQL**.

El paquete de entrega incluye:

- La carpeta del tema hijo `gamehub-child` (código propio del equipo).
- El archivo `gamehub.sql` (base de datos completa con contenido y datos de prueba).
- Este manual de instalación.

---

## 2. Requisitos previos

Antes de empezar, el equipo donde se instale debe disponer de:

| Software | Versión recomendada | Para qué |
|---|---|---|
| Sistema operativo | Windows 10 / 11 | Entorno de ejecución |
| XAMPP | Con PHP 8.1 o superior | Servidor Apache + MySQL + PHP |
| WordPress | 6.x | CMS base de la plataforma |
| Navegador web | Chrome, Firefox o Edge actualizado | Acceso a la plataforma |

> XAMPP incluye Apache, MySQL y PHP en un único instalador, por lo que no es necesario instalarlos por separado.

---

## 3. Instalación paso a paso

### Paso 1 — Instalar XAMPP

1. Descargar XAMPP desde [https://www.apachefriends.org](https://www.apachefriends.org) (versión con PHP 8.1 o superior).
2. Ejecutar el instalador y asegurarse de marcar los componentes **Apache**, **MySQL** y **phpMyAdmin**.
3. Instalar en la ruta por defecto `C:\xampp` (no instalar en "Archivos de programa" para evitar problemas de permisos).
4. Abrir el **Panel de Control de XAMPP** y pulsar **Start** en **Apache** y en **MySQL**. Ambos deben quedar en color verde.
5. Comprobar que funciona accediendo a `http://localhost` en el navegador.

> **Posible incidencia:** si Apache no arranca, suele deberse a que el puerto 80 está ocupado por otra aplicación. Cerrar dicha aplicación o cambiar el puerto de Apache resuelve el problema.

### Paso 2 — Colocar WordPress

1. Descargar WordPress desde [https://es.wordpress.org/download/](https://es.wordpress.org/download/).
2. Descomprimir el archivo. Se obtiene una carpeta llamada `wordpress`.
3. Copiar esa carpeta dentro de `C:\xampp\htdocs\` y **renombrarla a `gamehub`**.
   - La ruta final debe ser exactamente: `C:\xampp\htdocs\gamehub`
   - **Importante:** usar esta ruta exacta es fundamental para que la base de datos importada funcione correctamente (WordPress almacena la URL del sitio internamente).

### Paso 3 — Crear la base de datos

1. Acceder a `http://localhost/phpmyadmin`.
2. Pulsar **"Nueva"** en el menú izquierdo.
3. Crear una base de datos con el nombre **`gamehub`** y cotejamiento `utf8mb4_general_ci`.
4. Pulsar **"Crear"**.

### Paso 4 — Importar la base de datos del proyecto

Este paso carga todo el contenido y la configuración de GameHub (videojuegos, noticias, usuarios, ajustes, datos de prueba).

1. En phpMyAdmin, seleccionar la base de datos **`gamehub`** recién creada en el menú izquierdo.
2. Ir a la pestaña **"Importar"**.
3. Pulsar **"Seleccionar archivo"** y elegir el archivo `gamehub.sql` incluido en el paquete de entrega.
4. Dejar el resto de opciones por defecto y pulsar **"Continuar"**.
5. Esperar al mensaje de confirmación de importación correcta.

### Paso 5 — Configurar la conexión de WordPress

1. En la carpeta `C:\xampp\htdocs\gamehub`, localizar el archivo `wp-config-sample.php`.
2. Hacer una copia y renombrarla a `wp-config.php`.
3. Abrir `wp-config.php` con un editor de texto y configurar los datos de la base de datos:

   ```php
   define( 'DB_NAME', 'gamehub' );
   define( 'DB_USER', 'root' );
   define( 'DB_PASSWORD', '' );   // Vacío por defecto en XAMPP
   define( 'DB_HOST', 'localhost' );
   ```

4. Guardar el archivo.

> Si el paquete incluye ya un `wp-config.php` configurado, basta con colocarlo en la carpeta y omitir este paso.

### Paso 6 — Instalar el tema hijo

1. Copiar la carpeta `gamehub-child` (incluida en el paquete) dentro de:
   `C:\xampp\htdocs\gamehub\wp-content\themes\`
2. La ruta final debe ser: `C:\xampp\htdocs\gamehub\wp-content\themes\gamehub-child`

> El tema padre `Twenty Twenty-Four` viene incluido con WordPress por defecto, por lo que no es necesario instalarlo aparte. Si no estuviera presente, instalarlo desde *Apariencia → Temas → Añadir nuevo*.

### Paso 7 — Verificar la instalación

1. Acceder a la plataforma en `http://localhost/gamehub`.
2. Debe mostrarse la portada de GameHub con la noticia destacada, las últimas noticias y el Top Ranking.
3. Acceder al panel de administración en `http://localhost/gamehub/wp-admin`.

---

## 4. Plugins necesarios

La plataforma utiliza los siguientes plugins, que quedan incluidos en la base de datos importada. Si tras la instalación no estuvieran activos, activarlos desde *Plugins* en el panel:

| Plugin | Función |
|---|---|
| Advanced Custom Fields (ACF) | Campos personalizados de videojuegos y eventos (notas, fechas, etc.) |
| Custom Post Type UI | Tipos de contenido personalizados (Videojuego, Evento) |

---

## 5. Resolución de problemas frecuentes

| Problema | Causa probable | Solución |
|---|---|---|
| Apache no arranca en XAMPP | Puerto 80 ocupado | Cerrar la aplicación que usa el puerto o cambiar el puerto de Apache |
| La web aparece sin estilos o rota | Tema hijo no activo o ruta incorrecta | Comprobar que `gamehub-child` está en la carpeta de temas y activarlo en *Apariencia → Temas* |
| Página "no encontrada" en catálogo, ranking, etc. | Reglas de URL sin regenerar | Ir a *Ajustes → Enlaces permanentes* y pulsar *Guardar cambios* sin modificar nada |
| Las imágenes o enlaces apuntan mal | WordPress instalado en una ruta distinta a `C:\xampp\htdocs\gamehub` | Reinstalar usando la ruta exacta indicada |
| Los campos de videojuegos/eventos no se ven | Plugin ACF desactivado | Activar Advanced Custom Fields en *Plugins* |

---

## 6. Acceso a la plataforma

Tras la instalación, la plataforma queda accesible en las siguientes direcciones:

- **Sitio público:** `http://localhost/gamehub`
- **Panel de administración:** `http://localhost/gamehub/wp-admin`

Las credenciales de los usuarios de prueba (administrador y demás roles) se incluyen por separado junto con el paquete de entrega para facilitar la evaluación.
