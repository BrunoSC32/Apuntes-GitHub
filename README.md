# Apuntes-GitHub

Repositorio de apuntes sobre Git.

# Diapositiva 1: Introduccion y Configuraciones Basicas de Git

---

## 1. Que es Git?
- Es un **Sistema de Control de Versiones Distribuido (VCS)**.
- Permite:
  - Guardar versiones de archivos.
  - Mantener historial de cambios.
  - Trabajar de forma local sin depender de un servidor central.

---

## 2. Como nacio Git?
- Surge tras problemas con el sistema **BitKeeper**.
- Su creador, **Linus Torvalds**, decidio desarrollar una alternativa propia.
- Tiempo de desarrollo: **2 a 3 semanas**.
- Objetivo: un sistema rapido, eficiente y distribuido.

---

## 3. Como instalar Git?
- Sitio oficial: https://git-scm.com/install/

### Pasos
1. Descargar segun el sistema operativo: Windows, macOS o Linux.
2. Seguir la instalacion recomendada.

---

# Diapositiva 2: Estados de Git, Commits y Buenas Practicas

---

## 1. Los tres estados de Git

Git cataloga tus archivos en distintos estados a medida que avanzas en tu trabajo:

### Directorio de trabajo (modificado)
- Es tu carpeta local donde escribes o modificas tu codigo.
- Aqui Git observa tus archivos y los clasifica como:
  - **Untracked**: archivos recien creados, sin seguimiento.
  - **Modified**: archivos que Git ya conocía pero fueron alterados o eliminados.

### Stage area (preparado)
- Es un area de espera temporal donde seleccionas y preparas que archivos modificados deseas incluir en tu proximo guardado.

### Repositorio local (confirmado)
- Es el historial oficial.
- Los cambios aqui ya tienen un identificador (**hash**) y forman parte permanente de la historia del proyecto.

---

## 2. Comandos por estado

### En el directorio de trabajo
- Restaurar un archivo modificado a su estado original:
  - `git restore <archivo>`
- Evitar que Git haga seguimiento de ciertos archivos o carpetas:
  - Agregar su nombre completo al archivo `.gitignore`.

### En la stage area
- Agregar un archivo especifico:
  - `git add <archivo>`
- Agregar todos los archivos observados:
  - `git add .`
- Sacar un archivo del stage y devolverlo al estado anterior:
  - `git restore --staged <archivo>`

### En el repositorio local
- Confirmar los cambios y crear el punto de guardado:
  - `git commit -m "mensaje"`
- Deshacer el ultimo commit:
  - `git reset --soft HEAD~1`

---

## 3. Buenas practicas al hacer commits
- **Commits atomicos**: cada commit debe representar un cambio logico unico, pequeno y completo.
- **Frecuencia**: haz commit a menudo; es mejor tener varias iteraciones pequenas con mejoras especificas que un solo guardado masivo.
- **Estabilidad**: asegurate de que tus commits tengan sentido y no dejen tu proyecto sin funcionar.

---

## 4. Como escribir buenos mensajes de commit
- Usa verbos imperativos:
  - Inicia tus mensajes con verbos como `Add`, `Change`, `Fix` o `Remove`.
- Evita puntuacion final:
  - No uses punto final ni puntos suspensivos en el titulo del mensaje.
- Se conciso:
  - El mensaje no deberia superar los 50 caracteres; si es mas largo, considera dividir los cambios.
- Usa prefijos semanticos:
  - Estructura tu mensaje como `<tipo>: <descripcion>`.

### Prefijos comunes
- `feat`: nueva caracteristica para el usuario.
- `fix`: solucion de un bug o error.
- `docs`: cambios en la documentación.
- `style`: formato, espacios o tabulaciones que no afectan al funcionamiento del codigo.
- `refactor`: reestructuracion del codigo.
- `test`: agregado o modificacion de pruebas.
- `perf`: mejoras de rendimiento.
- `build`: cambios relacionados con compilacion o dependencias.
- `ci`: cambios en integración continua.

### Anadir contexto en el cuerpo
- Si necesitas explicar el porque de un cambio de forma extensa, usa `git commit` sin `-m` para abrir el editor.
- La primera linea sera el titulo del commit.
- Desde la segunda linea en adelante podras redactar el cuerpo con el contexto necesario.
