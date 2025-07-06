# Proyecto-Final-Programacion-II
## Introduccion del proyecto

Primero, como se especifico en los avances anteriores nuestro poryecto final es de Baches.
Nosotros queremos ayudar a la población del cantón Quito, en cuestión de dar una solución a los tantos baches que hay en la ciudad.
Nuestro programa consiste en que el usuario ingrese e inicie sesion con su nombre y se le desplegará un menú donde puede ver ingresar bache, lista de baches y lista firebase. 
Donde esto se explicara a continuación. 
Nuestro proyecto busca que nuestra ciudad y sus calles sean las más hermosas del Ecuador y también dar una gran ayuda ala ciudadania con este programa ya que va a ser organizado y así el municipio pueda trabajar de la mejor manera.

## Paquetes y Clases del proyecto
## Paquete **Interfaz**
### Clase FormularioBache 
La clase **FormularioBache** es una ventana gráfica (**JFrame**) que permite al usuario llenar un formulario para reportar un bache. Incluye campos para ingresar la calle principal, calle secundaria y una descripción del problema. También tiene un botón para seleccionar la ubicación en un mapa, lo cual carga automáticamente la dirección y coordenadas desde un archivo **ubicacion.txt**. Finalmente, al hacer clic en "Guardar", se valida la información y se crea un objeto **ReporteBache** que se guarda usando el servicio **RegistroBaches**. Esta clase gestiona tanto la interfaz visual como la lógica de validación y carga de datos desde el mapa.

![FB 1 ](https://github.com/user-attachments/assets/dd47adf6-195b-4a38-a43e-d86f09b3194a)
![FB 2](https://github.com/user-attachments/assets/b527d0ce-2168-4d2a-8b18-b918e6810376)
![FB 3](https://github.com/user-attachments/assets/74366ee1-d118-4825-9fee-45c72f85fac6)
![FB 4](https://github.com/user-attachments/assets/5e3e85e3-e95b-47e3-95a0-163902286025)
![FB 5](https://github.com/user-attachments/assets/8aad9bf9-bd9d-4c99-8707-5b06ab8797da)
### Clase IniciarSesion
La clase **IniciarSesion** es la **pantalla principal de inicio de sesión del sistema.** Permite al usuario ingresar su nombre en un campo de texto y pulsar el botón **"Iniciar sesión".** Si el nombre ingresado es **"municipio"**, se reconoce como **usuario del municipio** y se abre una ventana especial **(VentanaMunicipio)** para gestionar baches. Si se ingresa cualquier otro nombre, se abre el **menú principal normal (MenuPrincipal)** y se muestra un saludo personalizado. Si el campo está vacío, se muestra una advertencia. Esta clase actúa como **punto de entrada** (main) del programa y controla el acceso según el tipo de usuario.

![INICIAR 1 ](https://github.com/user-attachments/assets/916b53be-6b8a-4003-991b-691b55e0a891)
![INICIAR 2 ](https://github.com/user-attachments/assets/dbbdbf16-7f59-4cf8-a2a9-52f033c90db2)
### Clase JSBridge
La clase **JSBridge** actúa como un **puente de comunicación entre Java y JavaScript**. Es utilizada para recibir desde un **mapa HTML** (mediante una llamada desde JavaScript) los datos de la dirección seleccionada: **calle principal**, **calle secundaria**, **latitud** y **longitud**. Al recibir estos datos, los envía al formulario de reporte (**FormularioBache**) para que se llenen automáticamente los campos. Además, muestra un **mensaje de éxito** y **cierra la ventana del mapa**. Esta clase permite la integración entre la **interfaz gráfica en Java** y la **interacción del usuario con un mapa web**.

![JSBRIDGE ](https://github.com/user-attachments/assets/f0fb4291-4c6e-47f6-b806-8381b7211774)
### Clase ListaBaches
La clase **ListaBaches** muestra una ventana tipo **JFrame** que permite al usuario ver la lista de baches guardados localmente. Utiliza el servicio **RegistroBaches** para obtener los objetos **ReporteBache** desde el almacenamiento local. Los datos se presentan en un **JTextArea** de solo lectura, incluyendo el **ID**, la **latitud**, **longitud** y la **descripción** de cada bache. Esta clase es útil para revisar rápidamente los reportes realizados sin necesidad de acceder a la base de datos en la nube.

![LISTA DE BACHES](https://github.com/user-attachments/assets/b52d81af-0055-4792-8323-16a74bbf2fb1)
### Clase ListaBachesFirebase
La clase **ListaBachesFirebase** es una ventana **JFrame** que permite al usuario visualizar la lista de baches almacenados en la base de datos Firebase. Se conecta al nodo **baches** usando **FirebaseConfig** y escucha una única vez (**addListenerForSingleValueEvent**) para obtener los datos. Los objetos recuperados se interpretan como instancias de **ReporteBache** y se muestran en un **JTextArea**, incluyendo su **ID**, **latitud**, **longitud**, **descripción** y **estado**. Si ocurre un error en la carga, se muestra un mensaje de error en la interfaz. Esta clase es clave para acceder a la información remota almacenada en la nube.

![FIRBASE 1](https://github.com/user-attachments/assets/77e93b90-c10e-4c9a-8e17-03e74313a82a)
![FIRBASE 2](https://github.com/user-attachments/assets/edef616a-136b-40c3-8ee3-aedc591972bc)
### Clase MapaDireccionWindow
La clase **MapaDireccionWindow** abre una ventana gráfica en Java (**JFrame**) que contiene un mapa interactivo implementado en HTML mediante un **WebView** de JavaFX. Utiliza un **JFXPanel** para integrar el componente JavaFX dentro de Swing. Al cargar el archivo **mapa.html** desde la carpeta **Resources**, se muestra el mapa al usuario. Cuando el documento del mapa se carga completamente, se crea un puente **JSBridge** y se inyecta en la página web como el objeto **window.app**. Esto permite que, al seleccionar una dirección en el mapa, los datos se envíen automáticamente al formulario **FormularioBache**. Esta clase facilita la selección visual de una dirección sobre el mapa y su integración con la interfaz gráfica Java.

![MAPA DE DIRECCION](https://github.com/user-attachments/assets/af769e7d-93ae-4ab5-a1f6-1295c96e1319)
### Clase MapaInteractivo
La clase **MapaInteractivo** permite abrir el archivo **mapa.html** en el navegador predeterminado del sistema operativo. Utiliza la clase **Desktop** de Java para acceder al navegador y cargar el mapa ubicado en la carpeta **src/Resources**. Antes de abrir el archivo, se verifica que exista físicamente; si no se encuentra, lanza una excepción con un mensaje de error. Esta clase se usa como alternativa simple a JavaFX para mostrar el mapa, permitiendo que el usuario seleccione una ubicación directamente desde el navegador web.

![MAPA INTERACTIVO 1](https://github.com/user-attachments/assets/ddcf2520-b578-49cb-97b7-e54c15d2f658)
### Clase MapaSeleccion
La clase **MapaSeleccion** permite mostrar un mapa interactivo en una ventana Java (**JFrame**) utilizando un **JFXPanel** con **WebView** de JavaFX. Carga el archivo **mapa.html** desde la carpeta **Resources** y crea un puente entre JavaScript y Java usando una clase interna llamada **JSBridge**. Esta clase recibe la dirección seleccionada por el usuario en el mapa y se la comunica a través del patrón **Listener** definido por la interfaz **DireccionListener**. Al seleccionar una dirección, la ventana se cierra y se muestra un mensaje de confirmación. Esta implementación es útil cuando se desea manejar la dirección como una sola cadena y permite una comunicación directa JS → Java en tiempo real.

![MAPA DE SELECCION 1](https://github.com/user-attachments/assets/da28ff6c-ea69-4df3-82f7-919f8fc7fc4e)
![MAPA DE SELECCION 2 ](https://github.com/user-attachments/assets/74367c2e-4c2b-45f9-953c-8707becd0933)
### Clase MapaSelector
La clase **MapaSelector** permite abrir el archivo **mapa.html** directamente en el navegador predeterminado del sistema operativo. Utiliza la clase **Desktop** de Java para lanzar el navegador y mostrar el mapa interactivo desde la ruta **src/Resources**. Antes de abrirlo, verifica si el archivo realmente existe, y en caso contrario muestra un mensaje de error en la consola. Esta clase ofrece una forma sencilla de permitir al usuario seleccionar una ubicación en el mapa sin depender de componentes JavaFX, facilitando la interacción con HTML desde el navegador.

![MAPA SELECTOR ](https://github.com/user-attachments/assets/66a2bf5d-71f5-42fc-8757-cd72982277c3)
### Clase MenuPrincipal
La clase **MenuPrincipal** representa la pantalla principal del sistema una vez que el usuario ha iniciado sesión. Es una ventana **JFrame** que muestra un mensaje de bienvenida personalizado con el **nombre del usuario** y contiene cinco componentes: un saludo y cuatro botones. Los botones permiten al usuario: **reportar un bache**, **ver baches guardados localmente**, **ver baches almacenados en Firebase**, y **salir del sistema**. Cada botón abre una ventana distinta (**FormularioBache**, **ListaBaches**, **ListaBachesFirebase**) o termina la ejecución del programa. Esta clase actúa como centro de navegación para acceder a todas las funcionalidades del sistema.

![MENU PRINCIPAL ](https://github.com/user-attachments/assets/ab7b99da-9156-4695-a3b0-f64cc4591028)
### Clase VentanaMapa
La clase **VentanaMapa** crea una ventana interactiva en Java (**JFrame**) que permite al usuario seleccionar una ubicación directamente sobre un mapa HTML. Utiliza **JavaFX** embebido dentro de Swing mediante **JFXPanel**, y carga el archivo **mapa.html** desde la carpeta **Resources**. Una vez que el mapa se ha cargado completamente, se establece una conexión entre Java y JavaScript usando **JSBridge**, que se inyecta como el objeto **javaBridge** en el entorno web. Cuando el usuario selecciona una dirección, esta se envía automáticamente al formulario **FormularioBache**. Esta clase es clave para habilitar la selección de ubicación desde un mapa integrado dentro de la aplicación.

![VENTANA](https://github.com/user-attachments/assets/52c78d73-76c7-499f-ac97-31e43694d612)
### Clase VentanaMunicipio
La clase **VentanaMunicipio** permite al personal autorizado (como el municipio) actualizar el estado de un bache a "Bache arreglado" ingresando su **ID**. Es una ventana **JFrame** sencilla que contiene un campo de texto (**JTextField**) y un botón para confirmar la acción. Al hacer clic en "Aceptar", se conecta a Firebase a través de **FirebaseConfig** y busca el bache por su **id** en el nodo **baches**. Si lo encuentra, actualiza su campo **estado** de manera asíncrona usando **setValueAsync**. Esta clase es esencial para que el municipio gestione el seguimiento y solución de los reportes ciudadanos desde la aplicación.

![MUNICIPIO](https://github.com/user-attachments/assets/1cae8342-f7d9-4e4e-92cc-551e2f4282e6)
![MUNICIPIO 2 ](https://github.com/user-attachments/assets/f87e217a-e657-4550-bd73-ff92a10e1a2a)
## Paquete `Mapa`
### Clase `GoogleMapsEmbed`

![image](https://github.com/user-attachments/assets/9a416020-a15c-46c6-8486-56dfd2af440f)

El paquete `Mapa` contiene la clase responsable de integrar y gestionar los componentes relacionados con la visualización del mapa, específicamente utilizando Google Maps. Su objetivo principal es brindar funcionalidades que permitan representar ubicaciones geográficas de manera visual dentro del sistema, facilitando así la interacción del usuario con las coordenadas proporcionadas al momento de registrar un bache.

Este paquete contribuye directamente a la usabilidad del sistema, al permitir que los usuarios puedan ver o seleccionar visualmente la ubicación del bache que desean reportar, mejorando la precisión y experiencia del usuario.

![image](https://github.com/user-attachments/assets/7b486f79-86e1-475d-9071-6e028be046c7)

La clase `GoogleMapsEmbed` es una clase utilitaria dentro del paquete `Mapa`, cuya función principal es generar un fragmento de código HTML que permite mostrar un mapa de Google Maps directamente en la pantalla, centrado en una latitud y longitud específica.

Esta funcionalidad recibe una latitud y longitud como parámetros y genera un cuadro de mapa en formato HTML que se muestra directamente en la interfaz del sistema. El mapa permite visualizar la ubicación indicada sin necesidad de abrir una nueva pestaña del navegador.

Esto resulta especialmente útil para que los usuarios puedan ver directamente en el sistema la ubicación del bache que están reportando, lo que mejora tanto la precisión del reporte como la facilidad de uso de la plataforma.

## Paquete `Modelo`

![image](https://github.com/user-attachments/assets/ef011dff-6e74-4735-9c9e-13381e13ab9f)

El paquete `Modelo` define las clases que representan los datos principales del sistema, como los reportes de baches y sus ubicaciones. Estas clases establecen las estructuras y atributos que describen los elementos reales con los que trabaja el programa.

Este paquete es esencial para la arquitectura del sistema, ya que permite organizar y manipular la información de forma clara, coherente y reutilizable. Además, sirve como base para la lógica del sistema y su interacción con servicios externos como Firebase, facilitando el almacenamiento, consulta y visualización de los datos.

### Clase `ReporteBache`

![image](https://github.com/user-attachments/assets/974a3333-d56a-4ffb-b865-d24a1064653c)

![image](https://github.com/user-attachments/assets/75feceb4-254a-4e81-8f02-c349aa03ee56)

Es utilizada para registrar y almacenar los baches reportados por los ciudadanos, incluyendo toda la información necesaria para que el municipio pueda ubicarlos y dar seguimiento. Es uno de los componentes clave del modelo de datos, ya que interactúa directamente con Firebase y con la interfaz gráfica que permite llenar el formulario del reporte.

La clase `ReporteBache` representa un reporte específico de un bache en la vía pública y extiende la clase base `ReporteIncidencia`, lo que permite reutilizar atributos y comportamientos comunes entre distintos tipos de reportes.

**Responsabilidades principales:**

- Almacenar información clave como:
  - Descripción del bache.
  - Ubicación geográfica (latitud y longitud).
  - ID único generado automáticamente.
  - Estado del reporte (por defecto: Pendiente).
- Generar un resumen textual del reporte para su visualización o envío de notificaciones.
- Tiene un método privado que crea un ID corto de 5 dígitos aleatorios, útil para búsquedas o actualizaciones en la base de datos.

### Clase `ReporteIncidencia`

![image](https://github.com/user-attachments/assets/be69dae8-987d-4b2a-b7ab-dc9301bffcbf)

![image](https://github.com/user-attachments/assets/eda3386c-c5d3-499c-b178-b1a1a51e4128)

Esta clase permite aplicar los principios de la programación orientada a objetos, como la herencia y el polimorfismo, facilitando la creación de distintos tipos de incidencias con una base común. Gracias a `ReporteIncidencia`, el sistema puede extenderse fácilmente para incluir otros tipos de reportes más adelante, sin necesidad de duplicar código.

La clase `ReporteIncidencia` es una estructura abstracta que representa una incidencia geográfica, como un bache, accidente o semáforo dañado. No se utiliza directamente, sino que sirve como modelo base para otras clases, como `ReporteBache`.

**Características principales:**

- Es una clase abstracta, por lo que no puede instanciarse directamente.
- Obliga a las subclases a implementar métodos como `generarResumen()`.
- Define atributos comunes a cualquier tipo de incidencia:
  - `descripción`: texto que describe el problema.
  - `latitud` y `longitud`: coordenadas geográficas del evento.
- Incluye constructores compatibles con Firebase (constructor vacío) y con inicialización directa desde el sistema.
- Establece el método abstracto `generarResumen()`, que debe ser personalizado por cada subclase para generar un resumen textual de la incidencia.

### Clase `Ubicación`

![image](https://github.com/user-attachments/assets/88e4d75a-564a-41d1-abc0-fe0c65e6a9fb)

![image](https://github.com/user-attachments/assets/42a9c31b-38db-46a1-b010-bd67493efbdd)

![image](https://github.com/user-attachments/assets/e21280bf-b7a9-4e34-be75-571af41ca3bc)


La clase `Ubicación` representa una ubicación específica en el sistema, incluyendo:

- Calle principal
- Calle secundaria
- Latitud
- Longitud

Implementa el método `leerDesdeArchivo()`, que permite leer esta información desde un archivo de texto (`ubicacion.txt`), facilitando la integración entre el mapa interactivo y el formulario en Java.

Con esto, el sistema puede conectar el mapa interactivo con el formulario, insertando automáticamente la dirección seleccionada por el usuario y sus coordenadas exactas.

## Carpeta `Resources`

![image](https://github.com/user-attachments/assets/c855ae34-5cf2-417e-b1c1-51a1fbce2abc)

### Archivo `mapa.html`

![image](https://github.com/user-attachments/assets/4a245d88-df02-49f4-83e4-23d677bb6ce6)

![image](https://github.com/user-attachments/assets/6629eb42-8eb1-4878-9ea5-6a436524c025)

![image](https://github.com/user-attachments/assets/31e3f443-b3af-4493-b155-6428ee7aa975)

![image](https://github.com/user-attachments/assets/af913562-2f66-4220-8a30-6481c39d71e6)

![image](https://github.com/user-attachments/assets/7ae81839-6de5-4a81-a8cb-42dc72c36239)


Este archivo permite una interacción visual sencilla y amigable, lo que mejora significativamente la experiencia del usuario. Al guardar la ubicación seleccionada en un archivo de texto, facilita la integración automática con el formulario Java, permitiendo que los datos del mapa se transfieran directamente al sistema sin intervención manual, agilizando el proceso de registro.

El archivo `mapa.html` es una página web interactiva diseñada para que el usuario pueda seleccionar una ubicación directamente desde un mapa de Google Maps. Es fundamental para que el reporte de baches sea lo más preciso posible.

**Funcionalidades principales:**

1. Carga un mapa centrado en Quito (Ecuador) mediante la API de Google Maps.
2. Solicita al usuario seleccionar una ubicación en el mapa con un clic.
3. Cuando el usuario hace clic:
   - Obtiene automáticamente la latitud y longitud de ese punto.
   - Utiliza la geocodificación inversa para identificar la calle principal y secundaria correspondientes.
4. Con esa información, genera automáticamente un archivo llamado `ubicacion.txt` que contiene:
   - Calle principal
   - Calle secundaria
   - Latitud
   - Longitud
5. Descarga este archivo en el equipo del usuario y cierra automáticamente la ventana del mapa.

## Paquete `Servicio`

![image](https://github.com/user-attachments/assets/8b996c6e-bdcf-414a-bb1f-c226962cbc2e)


El paquete `Servicio` contiene las clases encargadas de realizar las operaciones principales del sistema, como guardar reportes, conectarse con Firebase, enviar correos y manejar la lógica central de comunicación entre la interfaz y la base de datos.

### Clase `BacheService`

![image](https://github.com/user-attachments/assets/ec232d3b-f557-4e1b-a094-82cefa2c7882)

![image](https://github.com/user-attachments/assets/69df3802-1f56-4c24-947e-011977e6a009)


Esta clase es esencial porque conecta la interfaz con la base de datos, gestionando el almacenamiento de reportes y manejando errores para mejorar la experiencia del usuario.

La clase `BacheService` es la encargada de guardar los reportes de baches tanto localmente como en la base de datos de Firebase. Implementa la interfaz `RegistroBaches`, que define los métodos que debe cumplir cualquier clase que maneje el registro de baches.

**Funciones principales:**

- `guardarBache(ReporteBache bache)`:
  - Genera un ID único.
  - Guarda el bache en una lista local para consulta inmediata.
  - Envía el bache a Firebase.
  - Muestra un mensaje de confirmación si la operación es exitosa.

- `obtenerBachesLocales()`:
  - Devuelve la lista de baches guardados localmente durante la sesión actual.

- `mostrarMensajeExitoFirebase()`:
  - Muestra una ventana emergente confirmando que el bache fue subido correctamente.



### Clase `FirebaseConfig`

![image](https://github.com/user-attachments/assets/1e0372fd-5b89-4d71-9643-1906cf6650b0)

![image](https://github.com/user-attachments/assets/00a47731-f59f-4e57-afdb-d09c72e2c15a)

Esta clase es fundamental para permitir que el sistema interactúe con Firebase, una plataforma en la nube donde se almacenan los reportes de baches.

La clase `FirebaseConfig` se encarga de establecer la conexión entre el sistema Java y la base de datos Firebase Realtime Database. Esta clase se utiliza como una configuración centralizada para inicializar la app de Firebase una sola vez durante la ejecución del programa.

### Interfaz `RegistroBaches`

![image](https://github.com/user-attachments/assets/538cd2cf-17ba-406e-8179-861d17b27a71)

Esta interfaz permite que el sistema sea modular y flexible, ya que cualquier clase que implemente `RegistroBaches` puede ser intercambiada sin afectar el resto del código.

La interfaz `RegistroBaches` define un contrato que deben cumplir todas las clases encargadas de registrar baches en el sistema. Es decir, especifica los métodos mínimos que una clase debe implementar si desea gestionar el almacenamiento de reportes de baches.

- `guardarBache(ReporteBache bache)`  
  Indica que la clase debe implementar la lógica para guardar un bache (local o en Firebase).

- `obtenerBachesLocales()`  
  Define que debe existir una manera de obtener todos los baches almacenados localmente durante la sesión actual.

- `mostrarMensajeExitoFirebase()`  
  Requiere un método para mostrar un mensaje de confirmación al guardar exitosamente en Firebase.


## Ejecucion del programa 

![image](https://github.com/user-attachments/assets/d6e6e855-4596-45d3-bd3f-e0883282ad3e)

Como se ve en la imagen la app se ejecuta desde el inicio de sesión. Despues le damos clic en run código y nos sale lo siguiente:

![image](https://github.com/user-attachments/assets/20f98d08-175b-44ff-9a54-4bb5637fd06b)

En ese apartado nos sale ingrese su nombre para iniciar sesión, podemos poner cualquier nombre y nos deja iniciar sesion, tambien se puso una restricción de inicio de sesion. Que consta en lo siguiente, si pone la palabra exclusivamente  Municipio, ingresa a otra ventana nueva que solo tiene accesso las autoridades, pero esto se explica después.

![image](https://github.com/user-attachments/assets/b5d29a3e-ac23-4354-8d7a-21b75faa4840)

De ejemplo tomamos el nombre de Nicolas Ramos y le damos en aceptar y nos sale ese mensaje que se ve en la imagen. Le damos clic en OK. 


![image](https://github.com/user-attachments/assets/4f25d8b4-4a20-4e87-ba4b-cc97c4917a7b)

y se nos abre un menú, donde esta:
-ReportarBache: que es donde se puede reportar el bache, le damos clic ahi y nos sale lo siguiente

![image](https://github.com/user-attachments/assets/8d7cc0b3-963d-4d09-b641-e7d02751e1ec)

Donde podemos ingresar manualmente la calle principal y secundaria de la dirección o a si prefiere de otra manera tenemos la opción de seleccionar en el mapa la ubicación, esa opcion es la más intuitiva.
Para entrar al mapa le damos clic en selccionar en el mapa y nos aparece un mensaje de las instrucciones que toca seguir en el mapa entonces le damos en ok. Y ya podemos navegar en el mapa.

![image](https://github.com/user-attachments/assets/3bf20574-3a9f-49a2-8936-218be48480d3)

Escojemos la ubicacion de la av. Amazonas y Alonso Pereira pero el mapa a veces no sabe detectar la calle secundaria y la ingresamos manualmente, tambien observamos que se nos descarga un .txt y es para que en la app al dar ok al mensaje 

![image](https://github.com/user-attachments/assets/2b05405e-0ca8-4dc0-9f96-3b82e3c2b6a4)

 A ese mensaje se llenen automaticamente las calles principales y secundarias, si nos sale en calle secundaria no encontrada, la podemos ingresar manualmente, ya que es un error del mapa, mas no de nuestro programa.
 
![image](https://github.com/user-attachments/assets/f5c7290a-0699-4d0e-bf34-54e16fb8ec20)

Como se ve en la imagen llenamos los campos que nos pide en este caso la descripcion y tambien para una mejor ubicacion le borramos el direccion no encontrada en calle secundaria y le agregamos manualmente una, le damos clic en guardar y nos sale el siguiente mensaje.

![image](https://github.com/user-attachments/assets/cd5d237a-a18a-4230-a99f-533b7379e2df)

![image](https://github.com/user-attachments/assets/e27ae9ae-5adf-4e60-a1d1-d66317ccbe01)

En esas imagenes se sube directamente a la base de datos de firebase y a la local. Y volvemos al menú principal.

-VerBaches(Local): Aqui se muestra todo lo que ingresamos, ademas de la longitud y latitud de la direccion que nos da el mapa, es la base de datos del programa y se ve asi:

![image](https://github.com/user-attachments/assets/c1df76dd-9ea7-4f85-9c80-899f3e755796)

Como se observa tambien aparece el estado: Pendiente eso quiere decir que todos los reportes bache que se pongan van a aparecer con el estado pendiente. Cerramos esa ventana y volvemos al menú principal.

-VerBachesFirebase: Aqui se abre una ventana donde le damos clic en ir a firebase y no sale la base de datos con los mismos datos de base local, pero en la nube.

![image](https://github.com/user-attachments/assets/78e6a79d-24fa-479b-b7c9-5f7158194311)

![image](https://github.com/user-attachments/assets/78d65d97-6117-40e4-a732-302c78521351)

Como se ve en la segunda imagen nos lleva al firebase pero aqui se nos salio de las manos ya que intentamos de todos los metodos posibles para que nos salga la info pero no pudimos y solo nos quedamos con la base de datos local de la app. Osea lo que se iba a hacer aqui lo vamos a aplicar en la VerBaches(Local).

-Volver al inicio de Sesion: VUelve al inicio de sesion para que el municipio entre.

![image](https://github.com/user-attachments/assets/0a4add5e-3703-4c2a-97cf-a23c8d1665c4)

Ponemos el unico nombre que permite acceder a la otra ventana que es Municipio

![image](https://github.com/user-attachments/assets/a6c96312-0bce-4430-ba19-fc148956c18c)

Le damos aceptar y nos sale el siguiente mensaje:

![image](https://github.com/user-attachments/assets/2290fd43-472c-4498-b904-ded36062d2d7)

Le damos en ok y entramos a la ventana, donde el municipio va a ingresar el ID del bache generado aleatoriamente por la app, cabe recalcar que es un ID unico de 5 digitos, donde el municipio ingresa ese ID para actualizar el estado del bache a arreglado.
Entonces ponemos el ID del bache que nos genero y estaba en VerBaches(local).

![image](https://github.com/user-attachments/assets/fc5141d3-2dbe-4faa-b9d1-e1d13e67c1a5)

Le damos clic en aceptar y nos sale lo siguiente:

![image](https://github.com/user-attachments/assets/943a5cb0-44ff-4251-a5cd-c6be28fdfaf0)

 Cuando le damos OK vuelve al iniciar sesion y unicamente debemos entrar con el nombre que ingreso el usuario, en este caso Nicolas Ramos
 
 ![image](https://github.com/user-attachments/assets/dcee09ae-fccb-4f60-9ec1-f211febb7029)
 
 Y entramos a VerBaches(Local), para constatar que ya se arreglo el estado del bache.
 
![image](https://github.com/user-attachments/assets/37605deb-1444-4152-8039-86418fadf4ef)

Efectivamente vemos que ya sale arreglado, cabe señalar que mientras se este ejecutando la app y siempre y cuando pongamos el nombre con el que ingreso el usuario al inicio vamos a tener su base de datos de los baches, pero si ingresa despues del municipio con otro nombre que en este caso no sea Nicolas Ramos, en VerBaches(Local), le va a aparecer vacio. Osea que cada usuario tiene una base de datos mientras se ejecute la app, si le ponemos en el boton salir ahi si se borra todo.

El usuario Nicolas Ramos puede ingresar los bache que quiera, como se a continuacion:

![image](https://github.com/user-attachments/assets/0271df95-8ffd-4c97-9059-112f05090300)

Le damos clic en guardar y nos vamos a VerBaches(Local)

![image](https://github.com/user-attachments/assets/103950b1-bbbe-4d17-9184-cca05e2dbcc3)

Y vemos que tambien esta el reporte del bache que agrego recien y el que ya esta arreglado.

Finalmente le ponemos en el boton salir y se cierra la app

![image](https://github.com/user-attachments/assets/423d1929-5d1b-4add-b4c4-a08116216867)

![image](https://github.com/user-attachments/assets/100da42e-7d69-4702-8122-50d43665c655)

Y listo.











