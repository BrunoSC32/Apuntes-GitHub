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

---

# Diapositiva 3: GitHub, SSH y Sincronizacion Remota

---

## 1. Que es GitHub y en que se diferencia de Git?
- **GitHub** es una plataforma en la nube y una red social para desarrolladores que permite alojar, gestionar y colaborar en proyectos de software.
- **Git vs GitHub**:
  - **Git** es la herramienta de control de versiones que crea los puntos de guardado locales.
  - **GitHub** es el servidor donde esos cambios se almacenan y comparten con otros.
  - GitHub utiliza Git, pero no son lo mismo.

---

## 2. Autenticacion: HTTPS vs SSH

### HTTPS
- Si usas HTTPS para clonar o interactuar con un repositorio, tendras que autenticarte con un token constantemente.
- Esto puede resultar molesto y poco practico.

### SSH
- SSH configura una llave entre tu computadora y GitHub.
- Te permite interactuar con el repositorio sin introducir credenciales cada vez.
- Es la practica recomendada.

---

## 3. Configuracion paso a paso de la llave SSH
- Para configurar tu llave SSH, ejecuta estos comandos en la terminal o en Git Bash en Windows.

### Generar la llave
- `ssh-keygen -t ed25519 -C "tu-correo@email.com"`

### Ver la llave publica
- `cat ~/.ssh/id_ed25519.pub`
- Debes copiar el texto que este comando devuelva.

### Vincular la llave en GitHub
- Ve a `Settings > SSH and GPG keys > New SSH key`.
- Pega la llave copiada.
- Asignale un nombre para identificar tu computadora.
- Guarda la configuracion.

### Verificar la conexion
- `ssh -T git@github.com`
- Este comando comprueba que la configuracion fue exitosa.

---

## 4. Crear, conectar y clonar repositorios

### Crear un repositorio en GitHub
- Ve a la pestana `Repositories`.
- Haz clic en `New`.
- Asignale un nombre.
- Elige su visibilidad: publico o privado.
- Presiona `Create Repository`.

### Conectar tu repositorio local con GitHub
- Si ya tienes un repositorio local con `git init` y al menos un commit, debes vincularlo al remoto con:
  - `git remote add origin git@github.com:TuUser/TuRepo.git`
- `origin` es el apodo local del servidor remoto.

### Cambiar a la rama principal
- `git branch -M main`

### Subir los cambios
- `git push -u origin main`

### Clonar un repositorio existente
- Para descargar el proyecto a tu computadora:
  - `git clone "git@github.com:TuUser/TuRepo.git"`

### Cambiar de HTTPS a SSH
- Si clonaste con HTTPS por error, puedes cambiar la URL remota con:
  - `git remote set-url origin "git@github.com:TuUser/TuRepo.git"`

### Verificar el remoto configurado
- Para ver a que repositorio esta conectado tu proyecto actual:
  - `git remote`

---

## 5. Sincronizar cambios (Push y Pull)

### Subir cambios (Push)
- Para enviar tus commits desde tu entorno local hacia GitHub:
  - `git push origin <rama>`

### Bajar cambios (Pull)
- Para traer actualizaciones y nuevos commits desde GitHub hacia tu entorno local:
  - `git pull origin <rama>`

---

# Diapositiva 4: Git Remote, Multiples SSH y Checkout

---

## 1. Gestion de remotos con Git Remote
- El comando `git remote` le indica a Git local a donde enviar o de donde traer informacion.
- Permite gestionar las conexiones con repositorios remotos en la nube.

### Comandos utiles
- Mostrar las URLs configuradas actualmente:
  - `git remote -v`
- Vincular el repositorio local con un nuevo remoto:
  - `git remote add <apodo> "url"`
- Cambiar la URL de un remoto existente:
  - `git remote set-url <apodo> "url"`

---

## 2. Multiples cuentas SSH
- Si tienes mas de una cuenta de GitHub, por ejemplo personal y trabajo, necesitas una llave SSH para cada una.
- Esto evita conflictos entre cuentas.

### Pasos para configurarlas

### Generar una nueva llave
- Usa una ruta especifica con `-f`:
  - `ssh-keygen -t ed25519 -C "micorreo@gmail.com" -f ~/.ssh/id_miname`

### Crear un archivo config
- Debes crear el archivo `config` dentro de la carpeta `.ssh`.
- Alli defines:
  - `Host`: apodo, por ejemplo `github-miname`
  - `HostName`: normalmente `github.com`
  - `User`: normalmente `git`
  - `IdentityFile`: ruta de la llave privada

### Verificar y clonar
- Verifica la conexion con:
  - `ssh -T git@github-miname`
- Para clonar con esa cuenta, reemplaza `github.com` por tu apodo:
  - `git clone git@github-miname:usuario/repo.git`

---

## 3. Configuraciones locales
- Git tiene una jerarquia de configuraciones.
- Las configuraciones locales tienen prioridad sobre las globales.

### Uso de configuracion local
- Para aplicar una configuracion solo al repositorio actual, usa `git config` sin el flag `--global`.
- Ejemplo:
  - `git config user.name "Mi nuevo Name"`

---

## 4. Viajes en el tiempo con Git Checkout
- `git checkout` permite mover el `HEAD`, que es tu puntero actual, hacia otro commit o hacia otra rama.

### Para que sirve
- Inspeccionar codigo de un commit antiguo.
- Restaurar archivos borrados.
- Experimentar sin afectar la rama principal.
- Cambiar de rama.

### Como viajar
- Para ir al pasado:
  - `git checkout <hash_antiguo>`
- Para volver al presente o a una rama:
  - `git checkout <rama>`

---

## 5. El estado Detached HEAD
- Normalmente, `HEAD` apunta a una rama movil.
- Cuando viajas a un commit antiguo, entras en estado **Detached HEAD**.
- Eso significa que `HEAD` ahora apunta a un commit fijo.

### Que implica
- Eres un espectador en ese punto de la historia.
- Si haces cambios y luego sales de ese estado sin crear una rama, esos cambios pueden perderse.

### Como conservar los cambios
- Crea una rama desde ese punto:
  - `git checkout -b rama_nueva`

---

## 6. Buenas practicas al viajar en el historial
- **Limpia tu directorio**:
  - Antes de viajar al pasado, haz commit de tus cambios actuales.
- **Crea ramas rapido**:
  - No trabajes mucho tiempo en `Detached HEAD`.
  - Si vas a experimentar en serio, crea una rama cuanto antes.
- **Usalo para aprender**:
  - Revisar commits antiguos en proyectos grandes ayuda a entender como fueron construidos paso a paso.
