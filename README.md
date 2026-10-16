# CI Pipeline para Laravel

Práctica de DGS - Emiliano Sánchez Pérez

## Objetivo
Automatizar la instalación de dependencias y la ejecución de pruebas de una aplicación Laravel mediante GitHub Actions.

## Tecnologías
- PHP 8.2
- Laravel 11
- Composer
- PHPUnit
- Git y GitHub
- GitHub Actions

## Requisitos
- PHP 8.2 o superior
- Composer
- Git
- Acceso al repositorio de GitHub

## Instalación local
1. Clonar el repositorio
2. Ejecutar `composer install`
3. Copiar `.env.example` a `.env`
4. Ejecutar `php artisan key:generate`
5. Crear el archivo vacío `database/database.sqlite`
6. Ejecutar `php artisan migrate`
7. Ejecutar `php artisan test`

## Integración continua
El workflow `.github/workflows/ci.yml` se ejecuta al enviar cambios a la rama `main` o al crear un pull request hacia `main`. Descarga el código, configura PHP 8.2, valida Composer, instala las dependencias, prepara el `.env` y ejecuta `php artisan test` usando SQLite en memoria.

## Pruebas
- `tests/Unit/ExampleTest.php`: prueba de ejemplo de Laravel.
- `tests/Feature/ExampleTest.php`: la página principal responde 200.
- `tests/Feature/HomePageTest.php`: verifica que la ruta `/` responda con un código de éxito.

Resultado esperado: 3 pruebas pasadas. Resultado obtenido: 3 pruebas pasadas en local y en GitHub Actions.

## Evidencias
- Ejecución exitosa (Prueba A): [link]
- Ejecución fallida controlada (Prueba B): [link]. Se cambió la prueba a `assertStatus(404)` y el log mostró "Expected response status code [404] but received 200."
- Ejecución exitosa después de la corrección: [link]

## Conclusiones
El pipeline detecta automáticamente cuando una prueba falla y muestra el error exacto en los registros de Actions. Al corregir la prueba y volver a subir los cambios, el pipeline pasó de nuevo. La integración continua permite detectar errores rápido y evita subir código roto a la rama principal.