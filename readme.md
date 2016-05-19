# Especificaciones Técnicas
En esta sección se encuentran las especificaciones técnicas del sistema.

Objetivos del Sistema
---------------

Maint Control es un sistema de gestion, asignación y control de las tareas de los tecnicos de mantenimiento de LAN al momento de realizar una mantención a un avión.

Glosario
---------------

### Usuario

#### Descripción
Es quien utiliza el sistema.

#### Atributos
* nombre.
* correo.
* contraseña.
* foto.
* bp. (identificador del usuario)

#### Relaciones
* Debe estar asociado a una [Base](http://localhost:8080/#especificaciones-tecnicas-glosario-base).


### Recurso
#### Descripción
Es un tecnico de mantenimiento.

#### Atributos
* nombre.
* correo.
* contraseña.
* foto.
* bp. (identificador del usuario)

#### Relaciones
* A un recurso se le pueden asignar multiples Labors.

### Labor
* Es una actividad o tarea.
* La cual puede ser asignada a un Recurso.
* un labor debe estar asociado a un Workpackage.

* productivo:

	* si un labor es productivo:
		* su termino es requerido para completar un Workpackage.
	* si un labor no es productivo:
		* su termino no es requerido para completar un Workpackage.

### Workpackage
* Es un conjunto de Labors.
* Un workpackage debe estar asociado a uno o mas Labors.
* un workpackage debe estar asociado a un Aircraft.


### Aircraft
* Es un avión.
* Un aircraft puede estar asociado a un workpackage.


### Base
* Es un Aeropuerto.
* 
* Un aircraft puede estar asociado a un workpackage.


# Casos de uso


En esta sección se encuentran los casos de usos del sistema Maint Control.


Web
---------------


Sección con los casos de uso correspondiente a parte web del sistema.


### Carga de Microplaning


El usuario realiza carga del microplaning de workpackages y labors
desde un archivo excel.

**Prioridad**
[Alta >][template]

**Actores**
[Usuario >][template]

**Pre Condiciones**

1. el usuario debe estar registrado en el sistema.
2. el usuario debe estar logado en el sistema.
3. el usuario debe tener perfil de floor planner,capacity planner o production manager.

	
**Flujo Básico**

1. El sistema pide al usuario que introduzca datos de la carga.

2. Usuario introduce los datos; en particular:
	* selecciona una BASE.
	* selecciona tipo de carga Microplanning.
	* selecciona archivo excel de Microplanning.
3. Usuario presiona boton upload para realizar carga al sistema.

**Post Condiciones**

	
1. En el sistema existiran nuevos registros; en particular:

   * Workpackages.
   * Labors asociados a un workpackage.
	  
	 			   		
**Excepciones**
	
1. internal error.



### Forecast


Al momento de editar el start y el end de un Labor, el Sistema Replanifica el start y el end de los labors dependientes de manera recursiva.

**Prioridad**
[Alta >][template]

**Actores**
[Usuario >][template]

**Pre Condiciones**

1. el usuario debe estar registrado en el sistema.
2. el usuario debe estar logado en el sistema.
3. el usuario debe tener permiso para editar un labor.
	
**Flujo Básico**

1. El Usuario Modifica el start y end de un labor.

2. 
3. Usuario presiona boton upload para realizar carga al sistema.

**Post Condiciones**

	
1. En el sistema existiran nuevos registros; en particular:

   * Workpackages.
   * Labors asociados a un workpackage.
	  
	 			   		
**Excepciones**
	
1. internal error.





[template]: https://github.com/rstacruz/flatdoc/raw/gh-pages/templates/template.html
