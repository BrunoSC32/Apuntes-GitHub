# Apuntes-GitHub
 Github note-taking repository

# Diapositiva 1: Introducción y Configuraciones Básicas de GIT

---

## 1. ¿Qué es GIT?
- Es un **Sistema de Control de Versiones Distribuido (VCS)**.
- Permite:
  - Guardar versiones de archivos 
  - Mantener historial de cambios 
  - Trabajar de forma local sin depender de un servidor central

---

## 2. ¿Cómo nació GIT?
- Surge tras problemas con el sistema **BitKeeper**.
- Su creador, Linus Torvalds, decidió desarrollar una alternativa propia.
- Tiempo de desarrollo: **2 a 3 semanas**.
- Objetivo: un sistema rápido, eficiente y distribuido.

---

## 3. ¿Cómo instalar GIT?
- Sitio oficial: https://git-scm.com/install/

### Pasos:
1. Descargar según el sistema operativo (Windows, macOS, Linux).
2. Seguir instalación recomendada.

### Verificación:
```bash
git --version

# Apuntes - Diapositiva 2: Estados de Git, Commits y Buenas Prácticas

**1. Los Tres Estados de GIT**

Git cataloga tus archivos en distintos estados a medida que avanzas en tu trabajo:

* **Directorio de Trabajo (Modificado):** Es tu carpeta local donde escribes o modificas tu código. Aquí Git observa tus archivos y los clasifica como *Untracked* (sin seguimiento, como archivos recién creados) o *Modified* (archivos que Git ya conocía pero han sido alterados o eliminados).

* **Stage Area (Preparado):** Es un área de espera temporal donde seleccionas y preparas qué archivos modificados deseas incluir en tu próximo guardado.

* **Repositorio Local (Confirmado):** Es el historial oficial. Los cambios aquí ya tienen un identificador (hash) y forman parte permanente de la historia de tu proyecto.

**2. Comandos por Estado**

* **En el Directorio de Trabajo:**
    * Para restaurar un archivo modificado a su estado original (ten cuidado, borra físicamente tus últimos cambios): `git restore <archivo>`.
    * Para evitar que Git haga seguimiento de ciertos archivos o carpetas, debes agregar su nombre completo al archivo `.gitignore`.

* **En la Stage Area:**
    * Para agregar un archivo específico a esta área: `git add <archivo>`.
    * Para agregar todos los archivos observados a la vez: `git add .`.
    * Para sacar un archivo del stage y devolverlo al estado anterior: `git restore --staged <archivo>`.

* **En el Repositorio Local:**
    * Para confirmar los cambios y crear el punto de guardado: `git commit -m "mensaje"`.
    * Para deshacer tu último commit: `git reset --soft HEAD~1`.

**3. Buenas Prácticas al hacer Commits**

* **Commits Atómicos:** Cada commit debe representar un cambio lógico único, pequeño y completo.
* **Frecuencia:** Haz commit a menudo; es mejor tener varias iteraciones pequeñas con mejoras específicas que un solo guardado masivo.
* **Estabilidad:** Asegúrate de que tus commits tengan sentido y **no dejen tu aplicación o proyecto sin funcionar**.

**4. Cómo escribir buenos mensajes de Commit**

* **Usa verbos imperativos:** Inicia tus mensajes con verbos como Add (añadir), Change (cambiar), Fix (arreglar) o Remove (eliminar).
* **Cero puntuaciones finales:** No desperdicies caracteres usando punto final ni puntos suspensivos.
* **Sé conciso:** Tu mensaje no debería superar los 50 caracteres; si es más largo, considera dividir los cambios en múltiples commits.
* **Usa prefijos semánticos:** Estructura tu mensaje como `<tipo de commit>: <descripción>` para hacer el historial más legible. Algunos prefijos comunes son:
    * `feat`: Nueva característica para el usuario.
    * `fix`: Solución de un bug o error.
    * `docs`: Cambios en la documentación.
    * `style`: Formato, espacios o tabulaciones que no afectan al usuario.
    * `refactor`: Reestructuración del código (ej. nombres de variables).
    * `test`: Agregado o modificación de pruebas.
    * `perf`, `build`, `ci`: Rendimiento, despliegue o integración continua.

* **Añade contexto en el cuerpo (si es necesario):** Si requieres explicar el porqué de un cambio de manera extensa, usa solo el comando `git commit` (sin `-m`) para que se abra un editor. La primera línea será tu título (con el prefijo), y desde la segunda línea en adelante podrás redactar el cuerpo con todo el contexto necesario, donde sí puedes aplicar reglas de puntuación.
