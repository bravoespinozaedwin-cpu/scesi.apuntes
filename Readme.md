# trabajo individual 
Bravo Espinoza Edwin Sebastian
## apuntes primera clase
### git
es un sistema de control de versiones distribuido vcs nos permite guardar archivos y las versiones de estos a lo largo del tiempo de manera local
un checkpoint de un videojuego para poder reponer en ciertos puntos de guardados creados, controlando asi su historial y poder volver atrás, también con un control de versiones.


### Como nacio git?
#### historia chisme
LINUX torvald creados de Linux, le llegaban ideas contribución por correo y el revisaba a mano, era un trabajo muy tedioso, asi que este con su comunidad decidio usar bitkeeper pero este era privaritivo, muy celoso. pero al no cumplir la regla le quitaron el acceso y entonces torvald se enojo , se encerro durante 2 a 3 semanas y creo Git

### config básicas
git config --global user.name "Tu Nombre"
git config --global user.email "tu@correo.com"
git config --global core.autocrlf true
## apuntes segunda clase
### estados de git
#### directorio de trabajo(modificado)
carpeta local, escribimos codigo pero aun no esta asegurado
dos tipos:
untracked lo ve pero no hay historial es  cuando se esta creando
modified ya existe historial donde modifique elimine o cambie de nombre
// cuaquiera que no este en gitignore para alguno de estos estados
##### volver atras
como hacer para que el archivo modificado vuelva atras 
git restore <archivo>  // este borra lo que hicimos asi que cuidado. y tambien se puede regresar a un archivo borrado.
#### stage area(preparado)
git add archivo para agregar uno en especifico a stage area
git add . agrega todos los archivos nuevos. todos los cambios
el area de espera le decimos a git : esto es lo que queremos guardar
para no mandar regresar
git restore --staged archivo
 el --staged //para solo dar un paso atras y no restaurar archivos eliminados si 
borra manualmentey recuepera eliminados
#### repositorio local (confirmado)
git commit -m "mensaje" 
ultima fase aqui es donde le decimos que guarde todos los cambios que esten staged a historial  //no se puede de untracked a modified primero debe pasar por guardado
el historial, tu cambiok
#### gitignore
dentro del gitignore se pone dentro lo que no se quiere cambiar o  quieren que acceda, dentro no se vera se pone dentro las rutas . tambien se puede poner extensiones , expresiones regulares * los comodines absolutas  casi todo menos imagenes
#### borrar ultimo commit
usamos el comando git reset --soft HEAD~1
volvemos al anterior commit y se borro nose recupera 
#### ejemplo
directorio de trabajo las cosas del supermercado
stage area = cosas que estan el carrito
repositorio local = cosas que compramos
#### Buenas practicas
cada cuanto hacer cambios,hacer commits cortos mejor si dividir cada commit, pero que tengas un significado
como escribirlos . deben ser crativos y con verbos imperativos
hacer commits en ingles
si usar . o comas, usar como maximo 50 palabras ser mas conciso.
git commit , va a un editor donde podemos poner mas texto mas especificaciones, poner cada prefijo respectivo -add prefijo -add prefijo em caso de que el commit sea demasiado grande en orden.
## apuntes de la tercera clase
### que es git hub?
github es una plataforma en la nube y red sociañ para desarrolladores el cual permite alojar, gestionar y colaborar en proyectos de software utilizando git
### git vs github
giy es el sistema de control de versiones, creando punto de guardados mientras que github es el servidor donde se almacenan y comparte github usa git
### como crear cuenta de git hub
*no con la cuenta institucional
*git controlador y git hub es lo que lo que te deja trabajar juntos.
#### crear repositorio
usar ssh-keygen -t ed25519 -C "correo"
git remote add origin sirve para apuntar directo 
automatizar enviado.
mover repositorios
se puede general y tambien llaves especificas
ssh en una maquina
### ssh /mas recomendable
Configuramos en nuestra PC/Laptop ssh para
comunicarnos con github, mediante una key la
cual al ponerla en Github no necesitara
pedirnos autenticarnos cada vez.
#### configuracion ssh
ssh-keygen -t ed25519 -C “tu-correo@email.com”

cat ~/.ssh/id_ed25519.pub  //llave publica


ssh -T git@github.com
### https
Cuando clonamos y queremos usar un repositorio
con HTTPS, este nos pedira autenticarnos cada
vez, hasta pidiendonos un token. Lo cual hace
que sea cansino y molesto.
### conectar reposit local con uno exitente en git hub
git remote add origin git@github.com:TuUser/TuRepo.git

git branch -M main

git push -u origin main

NOTA: PARA ESTO YA TIENES QUE HABER INICIALIZADO EL REPO LOCAL
(git init) Y TENER UN COMMIT INICIAL AL MENOS (git add . + git
commit -m “Initial commit”)
### clonar repositorio git
Para ello haces el comando:
git clone “git@github.com:TuUser/TuRepo.git”

Si por accidente lo hiciste con HTTPS:
git clone “https://github.com/TuUser/TuRepo.git”

Usa este comando para cambiar el puntero de github y no te
pida autenticación cada vez:
git remote set-url origin “git@github.com:TuUser/TuRepo.git”
 
 ver a que repositorio remoto esta conectado tu
repo:
git remote -v
### subir cambios
git push origin <rama> ///empujar commits al origen la rama de mi codigo
### bajar los cambios hechos
git pull origin <rama> traer commits al servidor del origin la rama del codigo
### aviso
crear perfil correcto por 5 puntos
## Apuntes de la clase 4

### Git remote

* Permite conectar tu repositorio local con uno remoto (como GitHub, GitLab, etc.).
* Comando principal para ver remotos:

  ```bash
  git remote -v
  ```
* Agregar un remoto:

  ```bash
  git remote add origin <url>
  ```
* Cambiar la URL de un remoto:

  ```bash
  git remote set-url origin <nueva-url>
  ```

---

### SSH (Secure Shell)

* Método seguro para autenticarte sin usar usuario/contraseña.
* Usa claves SSH (pública y privada).
* Generar clave:

  ```bash
  ssh-keygen -t ed25519 -C "tu_email@example.com"
  ```
* Se agrega la clave pública al servicio (ej. GitHub).
* Permite hacer `git push` y `git pull` sin autenticación manual constante.

---

### Múltiples remotes

* Un repositorio puede tener varios remotos (ej. `origin`, `upstream`).
* Ejemplo:

  ```bash
  git remote add upstream <url>
  ```
* Útil para trabajar con forks o múltiples servidores.
* Puedes hacer push o pull a cualquiera:

  ```bash
  git push origin main
  git pull upstream main
  ```

---

### Git checkout

* Se usa para cambiar de rama o restaurar archivos.
* Cambiar de rama:

  ```bash
  git checkout nombre-rama
  ```
* Crear y cambiar a una nueva rama:

  ```bash
  git checkout -b nueva-rama
  ```
* Restaurar archivo:

  ```bash
  git checkout -- archivo.txt
  ```

---


