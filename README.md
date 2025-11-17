Pokédex - TP Laboratorio 3
Este proyecto es una aplicación de Pokédex funcional desarrollada como parte del "TP Laboratorio 3". La aplicación consume datos de la PokéAPI y permite a los usuarios no solo consultar entradas de la Pokédex, sino también crear y gestionar equipos de Pokémon con atributos personalizados, y utilizar objetos en ellos.



🌟 Características Principales
La aplicación se divide en tres módulos principales accesibles desde la ventana de inicio:

Pokédex: Permite al usuario buscar cualquier especie de Pokémon por su nombre. Si se encuentra, la aplicación muestra todos sus atributos, estadísticas, sprite y datos de evolución. Si no se encuentra, se muestra un mensaje de error.



Gestión de Equipos: Los usuarios pueden crear nuevos equipos o buscar equipos existentes por su nombre. Todos los equipos se guardan persistentemente en un archivo .json. Dentro de un equipo, se pueden agregar nuevos Pokémon, modificar sus atributos (nivel, EVs, IVs, naturaleza, movimientos) o ver los Pokémon ya existentes.





Mochila y Objetos: Muestra los objetos cargados desde un archivo binario. Los usuarios pueden buscar un objeto y "usarlo" en un Pokémon específico seleccionando uno de sus equipos.


🛠️ Informe Técnico y Arquitectura
Carga de Datos
El programa se inicia cargando datos de tres fuentes distintas:

PokéAPI: Para todos los datos de las especies de Pokémon.

Archivo Binario: Para los datos de los objetos del juego.

Archivo JSON: Para los datos de los equipos creados por el usuario.

Arquitectura de Software
Carga Perezosa (Lazy Loading): Para evitar tiempos de inicio excesivos, la aplicación no carga todos los datos de todos los Pokémon al arrancar. Inicialmente, solo carga el nombre y la URL de la especie. Los datos completos de un Pokémon (incluyendo sus movimientos) solo se cargan desde la API cuando el usuario los solicita por primera vez. Este comportamiento se maneja a través de la interfaz ICargable.

Almacenamiento Genérico: Se creó una clase genérica AlmacenamientoDeDatos que funciona de manera similar a un Map, pero no permite la eliminación de datos. Se utiliza para gestionar las grandes colecciones de Pokémon y objetos.



Gestión de Equipos: Se utiliza un Set para la colección de equipos, asegurando que no existan equipos duplicados (la duplicidad se define por tener el mismo nombre).


Validación y Excepciones: La modificación de Pokémon (nivel, movimientos, EVs, etc.) está protegida por validaciones lógicas que lanzan excepciones personalizadas (ej. HabilidadNoPermitidaExeption ) si se ingresan datos inválidos, como exceder el límite de EVs, asignar un movimiento no aprendible o agregar más de 4 movimientos.


Diseño de Objetos: La clase Objeto es abstracta. Sus clases hijas (como MaquinasTecnicas y ObjetoEvolutivo) implementan el método usar de formas diferentes, utilizando ligadura dinámica para permitir la fácil expansión a nuevos tipos de objetos sin afectar el código existente.

Interfaz Gráfica (UI)
La interfaz gráfica se desarrolló con Java Swing. Se enfrentaron dificultades iniciales con IntelliJ, lo que llevó al equipo a migrar a Eclipse por su mejor soporte para la biblioteca gráfica. Se implementó un patrón de diseño donde cada ventana tiene su propio controlador, y estos se comunican entre sí para gestionar el flujo de la aplicación.





💻 Tecnologías y Recursos
Lenguaje: Java


Interfaz Gráfica: Java Swing 



Control de Versiones: Git y GitHub 


IDE: Eclipse 

Datos Externos:


PokéAPI 

Recursos de Apoyo:


Stack Overflow 


Javatpoint (Documentación Java/Swing) 


Visual Paradigm (Para UML) 

👨‍💻 Autores
Bianca Nahuel 

Corso Tomas 

Martino Gonzalo 


Profesor: Gonzalo Benoffi
