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
dice la dirrecion a la que nuestra nuve debe enviar o traer informacion
* Permite conectar tu repositorio local con uno remoto (como GitHub, GitLab, etc.).
* Comando principal para ver remotos:
git remote -v
 (Nos permite ver las URLs exactas dondeapunta nuestro repositorio)

git remote add <apodo> “url” / apodo como originjj 
(Vincula nuestro repo local
con uno en la nube.)

git remote set-url <apodo> “url” 
(Cambia la url dondeapunta nuestro repositorio)como de https a ssh

### Multiples SSH
interconectar ssh a mi github
cada tunel tiene su cerrojo su propia llave,  entonces si hay multiples ssh , un ssh para cada puerta y cuenta

#### configurar multiples ssh
ir donde esta mi ssh y ahi poner
Paso 1. Generamos el sshkey en con
otro nombre:



ssh-keygen -t ed25519 -C
"micorreo@gmail.com" -f ~/.ssh/id_miname

Paso 2. Creamos un archivo config
para que no choquen las key
Cuenta Personal (la de siempre)
Host github.com
HostName github.com
User git
IdentityFile ~/.ssh/id_ed25519
Cuenta del otro correo
Host github-miname
HostName github.com
User git
IdentityFile ~/.ssh/id_miname

host: es el apodo o alias  de la conexion depues de git@
hostName: direccion real donde nos conectamos siempre la misma
user: nombre del usuarion para git hub siempre es git
identity file ruta exacta hacia la llave que usara el host

Paso 3. Para verificar si funciona
ejecutamos el comando:

ssh -T git@github-miname
### Configuraciones Locales
Las configuraciones locales se imponen a las globales, y
estas solo funcionan para el repositorio en el que se aplican.
Para hacer configuraciones locales lo que se debe hacer es
lo mismo que en las globales pero sin el flag --global:

git config user.name "Mi nuevo Name"
git config user.email "micorreo@gmail.com"
tienen jerarquia 
system level
global level
local level
### git checkout
Es el comando que nos permite desplazar el HEAD
(nuestro puntero o "lector" actual) hacia un punto
específico de la historia o a una rama distinta.  ver atras
¿Para qué sirve?
Inspeccionar: Ver cómo era el código en un
commit antiguo.
Restaurar: Recuperar archivos que borramos o
cambiamos.
Experimentar: Probar cambios sin arruinar la
rama principal.
Cambiar: Saltarnos de una rama a otra (ej. de
main a desarrollo)


### commit en atras
no se crea una paradoja sin embargo nos dira al volver al main que tenemos un commit suelto si queremos podemos crear una rama
git checkout -b feature luego nombreexperimental
volvemos al main 
y para verlo hacemos
git log --graph --oneline --all
aqui se vera las demas ramas de la que estamos generemos una bifurcacion

### buenas practicas del checkout
no trabajar mucho en detached head
Si vas a escribir más de dos líneas, mejor crea una
rama de una vez.
antes de ir al pasado hacer commit  antes de viajar guardar la partida
se usa para aprender de proyectos grande viendo asi su proceso
no te deja ir sin el punto de guardado

## apuntes clase 5
### ramas 
se crean bifurcaciones ramas sin afectar el original
### comandos
git branch   //lista todas las ramas que tenemos y nos muestra en cual estamos
git branch nombredelanuevarama // creamos otra rama
git log --grapf --online -all 
ver commits 
para eliminar averiguar en windows
//head es en donde estas y main es hasta donde subiste al repositorio remoto
git checkout nos permite movernos
git switch es para moverse
git checkout igual pero muchas mas opciones
git branch -D nombrerama para eliminar
//averiguar mas comandos
git status
### gitflow  es un flujo de trabajo
un framework
nos da reglas establecidas y trabajar de forma ordenada

