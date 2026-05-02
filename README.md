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

### Pasos:
1. Descargar segun el sistema operativo: Windows, macOS o Linux.
2. Seguir la instalacion recomendada.

---

# Diapositiva 2: Estados de Git, Commits y Buenas Practicas

---

## 1. Los tres estados de Git
- Git clasifica tus archivos en distintos estados mientras trabajas.

### Directorio de trabajo (Modificado)
- Es tu carpeta local donde escribes o modificas tu codigo.
- Aqui Git detecta archivos en estados como:
  - **Untracked**: archivos nuevos sin seguimiento.
  - **Modified**: archivos que ya existian en Git y fueron cambiados.

### Stage area (Preparado)
- Es un area temporal donde eliges que cambios quieres incluir en el proximo commit.

### Repositorio local (Confirmado)
- Es el historial oficial del proyecto.
- Los cambios guardados aqui ya tienen un identificador (**hash**) y forman parte de la historia.

---

## 2. Comandos por estado

### En el directorio de trabajo
- Restaurar un archivo modificado a su estado original:
  - `git restore <archivo>`
- Evitar que Git haga seguimiento de archivos o carpetas:
  - Agregar sus nombres al archivo `.gitignore`.

### En la stage area
- Agregar un archivo especifico:
  - `git add <archivo>`
- Agregar todos los archivos observados:
  - `git add .`
- Quitar un archivo del stage:
  - `git restore --staged <archivo>`

### En el repositorio local
- Confirmar los cambios:
  - `git commit -m "mensaje"`
- Deshacer el ultimo commit sin perder cambios:
  - `git reset --soft HEAD~1`

---

## 3. Buenas practicas al hacer commits
- **Commits atomicos**: cada commit debe representar un cambio logico unico y completo.
- **Frecuencia**: es mejor hacer commits pequenos y seguidos que un solo cambio grande.
- **Estabilidad**: cada commit deberia dejar el proyecto en un estado funcional.

---

## 4. Como escribir buenos mensajes de commit
- Usa verbos en imperativo:
  - Ejemplos: `Add`, `Change`, `Fix`, `Remove`.
- Evita puntuacion final:
  - No uses punto final en el titulo del commit.
- Se conciso:
  - Intenta que el mensaje no supere los 50 caracteres.
- Usa prefijos semanticos:
  - Formato recomendado: `<tipo>: <descripcion>`.

### Prefijos comunes
- `feat`: nueva funcionalidad.
- `fix`: correccion de errores.
- `docs`: cambios en documentacion.
- `style`: cambios de formato sin impacto funcional.
- `refactor`: reestructuracion del codigo.
- `test`: cambios o agregado de pruebas.
- `perf`: mejoras de rendimiento.
- `build`: cambios de compilacion o dependencias.
- `ci`: cambios de integracion continua.

### Anadir contexto en el cuerpo
- Si necesitas explicar mejor el cambio, usa `git commit` sin `-m`.
- La primera linea sera el titulo del commit.
- Desde la segunda linea podras agregar el contexto necesario.
