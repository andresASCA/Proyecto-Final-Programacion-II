# Proyecto-Final-Programacion-II
## Introduccion del proyecto

Primero, como se especifico en los avances anteriores nuestro poryecto final es de Baches.
Nosotros queremos ayudar a la población del cantón Quito, en cuestión de dar una solución a los tantos baches que hay en la ciudad.
Nuestro programa consiste en que el usuario ingrese e inicie sesion con su nombre y se le desplegará un menú donde puede ver ingresar bache, lista de baches y lista firebase. 
Donde esto se explicara a continuación. 
Nuestro proyecto busca que nuestra ciudad y sus calles sean las más hermosas del Ecuador y también dar una gran ayuda ala ciudadania con este programa ya que va a ser organizado y así el municipio pueda trabajar de la mejor manera.

## Paquetes y Clases del proyecto

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



















