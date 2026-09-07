# Lógica & Algoritmos II — Proyecto Java POO

Esqueleto fundacional de un proyecto Java con POO para la asignatura **Lógica &
Algoritmos II** (Universidad de la Amazonia, Ingeniería de Sistemas, Semana 1).
Define una arquitectura en capas, los estándares de codificación del curso y una
entidad de ejemplo lista para reemplazar por la entidad real del equipo.

> **Resultado esperado:** al abrir el proyecto y ejecutar `Main`, se imprime el
> estado de un sensor y sus operaciones por consola. No requiere dependencias.

## Ruta rápida

1. **Abrir en NetBeans** — File → New Project → Java with Ant → *Java Project
   with Existing Sources* → seleccionar la carpeta raíz del proyecto.
2. **Ejecutar** — clic derecho sobre `Main.java` → *Run File*.
3. **Verificar** — la consola muestra el estado y el comportamiento del sensor.

## Estructura

```
.
├── .gitignore                       # Reglas de control de versiones
├── README.md                        # Este documento
├── Docs/                            # Material del curso (guías, PDF)
├── openspec/                        # Especificación del proyecto
└── src/
    └── co/edu/uniamazonia/logica2/
        ├── Main.java                # Punto de entrada (demo)
        └── modelo/
            └── SensorAmbiental.java # Entidad de ejemplo (plantilla)
```

## Arquitectura en capas

El proyecto se organiza por paquete, de simple a escalable. La idea central es
**empezar por el "Mundo del Problema"**: primero las entidades, después la lógica
y la infraestructura.

| Capa | Paquete | Responsabilidad | Estado |
|------|---------|-----------------|--------|
| `modelo` | `co.edu.uniamazonia.logica2.modelo` | Entidades del dominio del problema | Creada ahora |
| `servicio` | `co.edu.uniamazonia.logica2.servicio` | Lógica de negocio | Futura |
| `persistencia` | `co.edu.uniamazonia.logica2.persistencia` | Acceso a datos | Futura |
| `vista` | `co.edu.uniamazonia.logica2.vista` | Presentación / consola | Futura |
| `util` | `co.edu.uniamazonia.logica2.util` | Helpers transversales | Futura |

**Justificación:** modelar primero las entidades obliga a entender el problema
antes de escribir lógica. Las capas `servicio` y `persistencia` se agregan cuando
el modelo esté estable, y `vista` se conecta al final. Este orden evita acoplar
la lógica de negocio a la interfaz o a un mecanismo de almacenamiento concreto.

## Convenciones de codificación

Estándares obligatorios de la guía del curso. Registro neutral y profesional.

| Elemento | Regla | Ejemplo |
|----------|-------|---------|
| Clase | Sustantivo en singular, UpperCamelCase | `SensorAmbiental`, `Guardabosques` |
| Atributo | `private`, lowerCamelCase | `private String ubicacion;` |
| Método | `public`, verbo en infinitivo, lowerCamelCase | `registrarLectura()`, `calibrar()` |
| Tipos | Coherentes con el dato | `String`, `int`, `double`, `boolean` |
| Encapsulamiento | Atributos privados + getters/setters | `getNivelBateria()` / `setNivelBateria(...)` |

Notas:

- Para atributos `boolean`, el getter se nombra con `is` (convención JavaBeans):
  `isActivo()` en lugar de `getActivo()`.
- Los comentarios Javadoc se escriben en español, sin jerga regional.

## Entidad de ejemplo: `SensorAmbiental`

`src/co/edu/uniamazonia/logica2/modelo/SensorAmbiental.java` es una **plantilla
de referencia**, no la entidad definitiva. Ilustra todos los estándares:

- 4 atributos privados con tipos coherentes: `identificador` (String),
  `ubicacion` (String), `nivelBateria` (double), `activo` (boolean).
- Constructor que inicializa todos los atributos.
- Getters y setters para cada atributo.
- 3 métodos de comportamiento: `registrarLectura()`, `emitirAlerta()`, `calibrar()`.

Reemplácela por la entidad real del equipo cuando el problema esté definido.

## Abrir en NetBeans

1. File → **New Project**.
2. Categoría *Java with Ant* → *Java Project with Existing Sources*.
3. En *Project Folder*, seleccionar la carpeta raíz del proyecto.
4. NetBeans genera `build.xml` y la carpeta `nbproject/` automáticamente
   (no deben crearse a mano).

## Compilar y ejecutar desde CLI

Verificación manual con JDK 21 (los acentos exigen `-encoding UTF-8`):

```powershell
& "C:\Program Files\Microsoft\jdk-21.0.12.101-hotspot\bin\javac.exe" -encoding UTF-8 -d build src/co/edu/uniamazonia/logica2/Main.java src/co/edu/uniamazonia/logica2/modelo/SensorAmbiental.java
& "C:\Program Files\Microsoft\jdk-21.0.12.101-hotspot\bin\java.exe" -cp build co.edu.uniamazonia.logica2.Main
```

## Checklist de verificación

- [ ] `javac` compila sin errores con `-encoding UTF-8`.
- [ ] `Main` imprime el estado inicial, las operaciones y el estado final.
- [ ] Los atributos están marcados `private` y expuestos vía getters/setters.
- [ ] Las clases usan UpperCamelCase y los métodos verbos en infinitivo.

## Roadmap

- [ ] Reemplazar `SensorAmbiental` por la(s) entidad(es) real(es) del equipo.
- [ ] Agregar la capa `servicio` con la lógica de negocio.
- [ ] Agregar la capa `persistencia` para guardar/cargar datos.
- [ ] Conectar la capa `vista` (menú por consola).
- [ ] Incorporar JUnit para pruebas unitarias de las entidades y servicios.
- [ ] Documentar cada entidad con su Javadoc correspondiente.
