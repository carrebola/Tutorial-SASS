# Guía Práctica de Sass: Mejora tu CSS

## Introducción a Sass

Sass (Syntactically Awesome Stylesheets) es un preprocesador de CSS que extiende las capacidades de CSS con características avanzadas como variables, anidamiento, mixins, funciones y herencia. Estos beneficios hacen que la escritura y el mantenimiento de hojas de estilo sea más eficiente y ordenada.

A continuación, aprenderás cómo empezar a trabajar con Sass, junto con un ejemplo sencillo para que puedas practicar.

## Paso 1: Instalación de Sass

Antes de comenzar a usar Sass, necesitas instalarlo. La forma más fácil es a través de npm (Node Package Manager). Si ya tienes Node.js instalado, ejecuta el siguiente comando en la terminal:

```bash
npm install -g sass
```

Este comando instalará Sass de manera global en tu sistema.

## Paso 2: Crear Archivos Sass

Sass utiliza archivos con extensión `.scss`. Vamos a crear dos archivos para nuestro ejemplo:

1. `styles.scss`: Este será nuestro archivo Sass donde escribiremos los estilos.
2. `index.html`: Un archivo HTML sencillo donde aplicaremos los estilos.

## Paso 3: Escribir Código Sass

Vamos a escribir algunos estilos en nuestro archivo `styles.scss`.

```scss
// Variables
// Este color primario se usa como fondo en el cuerpo del documento. Puedes cambiarlo aquí para ajustar el esquema de color globalmente.
$primary-color: #3498db;
// Este color secundario se usa para los enlaces. Puedes modificarlo para cambiar el estilo de los enlaces en todo el sitio.
$secondary-color: #2ecc71;
// Esta variable define la fuente utilizada en el cuerpo del documento. Puedes agregar o cambiar las fuentes según tus preferencias.
$font-stack: 'Helvetica, Arial, sans-serif';

// Estilo general del cuerpo
// Este bloque aplica los estilos generales al cuerpo del documento. Incluye propiedades como el fondo, la fuente y el color del texto.
body {
  font-family: $font-stack;
  background-color: $primary-color;
  color: white;
  padding: 20px;
}

// Anidamiento de selectores
nav {
  ul {
    list-style: none;
    padding: 0;
  }

  li {
    display: inline-block;
    margin-right: 15px;
  }

  a {
    text-decoration: none;
    color: $secondary-color;
    // Cambia el color del enlace cuando el usuario pasa el ratón por encima, para mejorar la experiencia de usuario visualmente.
    &:hover {
      // La función `darken()` toma un color y lo oscurece en un porcentaje determinado. En este caso, el color secundario se oscurece un 10% para resaltar el efecto hover.
      color: darken($secondary-color, 10%);
    }
  }
}
```

En este ejemplo:

- Hemos creado variables (`$primary-color`, `$secondary-color`, `$font-stack`) para que sea más fácil cambiar los valores globalmente.
- Hemos anidado los selectores dentro de `nav` para simplificar y mejorar la legibilidad del código.
- Utilizamos `&:hover` para definir el estilo al pasar el ratón por encima de los enlaces.

## Paso 4: Compilar Sass a CSS

Sass necesita ser compilado a CSS para que los navegadores puedan interpretarlo. Para compilar el archivo `styles.scss` a CSS, ejecuta el siguiente comando en la terminal:

```bash
sass styles.scss styles.css
```

Esto generará un archivo `styles.css` que puedes enlazar en tu HTML.

> **Nota**: Si te aparece un error relacionado con la ejecución de scripts deshabilitada, como el siguiente:
>
> ```
> sass : No se puede cargar el archivo C:\Users\Carlos Arrebola\AppData\Roaming\npm\sass.ps1 porque la ejecución de scripts está deshabilitada en este sistema.
> ```
>
> Puedes solucionarlo cambiando la política de ejecución en PowerShell. Abre PowerShell como administrador y ejecuta el siguiente comando:
>
> ```powershell
> Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned
> ```
>
> Esto permitirá ejecutar el script de Sass sin problemas.

## Paso 5: Crear el Archivo HTML

Ahora, crea un archivo `index.html` para ver los estilos aplicados.

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Ejemplo Sass</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <nav>
    <ul>
      <li><a href="#">Inicio</a></li>
      <li><a href="#">Servicios</a></li>
      <li><a href="#">Contacto</a></li>
    </ul>
  </nav>
  <h1>Hola, este es un ejemplo de Sass!</h1>
</body>
</html>
```

## Paso 6: Verificar el Resultado

Abre el archivo `index.html` en tu navegador. Deberías ver el fondo con el color primario, el texto blanco y los enlaces estilizados con el color secundario.

## Características Adicionales de Sass

- **Mixins**: Puedes reutilizar bloques de código para mantener tu CSS limpio y eficiente.
  ```scss
  @mixin flex-center {
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .container {
    @include flex-center;
    height: 100vh;
  }
  ```

- **Funciones**: Sass tiene funciones predefinidas como `darken()`, `lighten()`, entre otras, que te ayudan a manipular colores y valores de manera más eficiente.

## Funciones Más Interesantes de Sass

Sass ofrece una variedad de funciones útiles para trabajar con colores, números y cadenas de texto. Algunas de las funciones más interesantes son:

- **`darken($color, $amount)`**: Oscurece un color en el porcentaje indicado.
- **`lighten($color, $amount)`**: Aclara un color en el porcentaje indicado.
- **`mix($color1, $color2, $weight)`**: Mezcla dos colores en una proporción determinada.
- **`percentage($value)`**: Convierte un valor decimal en un porcentaje.
- **`abs($number)`**: Devuelve el valor absoluto de un número.

### Crear Funciones Propias

Además de las funciones predefinidas, también puedes crear tus propias funciones en Sass para reutilizar lógica específica. Aquí tienes un ejemplo de cómo crear una función personalizada:

```scss
@function calcular-rem($pixels) {
  @return $pixels / 16 * 1rem;
}

.container {
  width: calcular-rem(320px);
  padding: calcular-rem(16px);
}
```

En este ejemplo, hemos creado una función `calcular-rem` que convierte un valor en píxeles a `rem`, lo cual es útil para trabajar con unidades relativas en CSS. Puedes llamar a esta función como cualquier función de Sass para realizar conversiones en tu hoja de estilo.

## Conclusión

Sass es una herramienta poderosa para mejorar la productividad y la calidad del código CSS. Te permite escribir estilos más organizados, reutilizables y mantenibles. Con este ejemplo básico, ya tienes una idea de cómo comenzar a usar Sass en tus proyectos. Aprovecha las características avanzadas de Sass para llevar tu CSS al siguiente nivel y hacer que tu flujo de trabajo sea mucho más eficiente.

