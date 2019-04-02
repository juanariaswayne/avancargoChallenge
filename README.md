# avancargoChallenge
Base RN proyect for Avancargo Challenge
Proyecto Avancargo Challenge
------------------------------------------------------------------------------------

Se crea la estructura base de un proyecto React Native.

Dentro de la carpeta app vamos a mantener la estructura de todo nuestro proyecto, ahora vamos
a explicar un poco el porque de dicha arquitectura elegida.

--android
--app
-----assets
-----components
-----modules
-----services
-----store
-----views
-----config
--ios

App -> Es la carpeta raiz de nuestra aplicacion.

Assets -> Aca contengo las imagenes, iconos y fuentes de la aplicacion de forma global.
Components -> Aca voy a poner todos los componentes compartidos de la app, como por ejemplo un spinner button... En si son componentes que no tienen logica y son facilmente reutilizables.

Components -> Aca contengo los componentes globales de la aplicacion, los que pueden ser reutilizados varias veces y no tienen una logica particular para cada vista... como por ejemplo un spinner button, o un header.

Modules -> Aca pongo las funciones que no tienen una vista especifica y que necesitan ser reutilizadas a lo largo de la app. En general pueden ser encontradas como un paquete npm, pero en caso de ser algo muy especifico se puede crear en este directorio nuestro propio modulo.

Services -> Aca tengo los diferentes servicios que van a conectar con los diferentes EndPoint y asi poder mantener la logica de conexion y procesamiento de data en un solo lugar.
Por ejemplo AuthService.js

Store -> Lo uso para mantener la misma informacion global necesaria para todos los componentes.

Config -> Aca suelo mantener las configuraciones necesarias de la aplicacion, por ejemplo las variables de entorno, o rutas de la app.

Views -> Aca pongo todas las pantallas que va a tener nuestra app.

Dentro de cada vista me parece importante tener en cuenta los siguientes aspectos:

- Mantener la logica de Redux dentro de cada vista, de la experiencia que tuve manejando aplicaciones con muchas pantallas detecte que no es conveniente usar la logica comun teniendo una carpeta para los actions, otra para los reducers, states etc. ya que si tenemos por ejemplo mas de 20 pantallas esto puede llegar a ser confuso o desordenar el proyecto. Entonces si mantenemos todo bajo la misma carpeta de la vista se hace mucho mas simple el manejo.

Tambien me parece importante poder separar los estilos para IOS y Android ya que muchas veces podriamos necesitar tener vistas separadas para adaptar de la mejor forma el contenido en cada uno de los sistemas operativos.

En este caso decidi usar la libreria Redux para el manejo de estados de la aplicacion, seleccione esta libreria y no otras como Mobx ya que considero que va a ser una App compleja y va a necesitar escalar lo suficiente ademas de ser una libreria mas conocida en el mercado y mas facil de afrontar si el dia de mañana debe ser mantenida por un equipo de desarrollo mas grande.

En el caso de no querer usar una libreria para manejar los estados de la aplicacion, deberiamos tener nuestros propios providers dentro de la carpeta modules.

---------------------------------------------------------------------------------------------
Para Tener en cuenta...

Para poder darle estilos a nuestos componentes estoy usando una libreria externa
llamada styled-components, ya que me va a permitir trabajar los estilos de una forma mas
natural como si fuera css, aunque tambien podria usarse de la forma que propone React con 
StyleSheet.create.

Es importante tener en cuenta los diferentes tamaños de pantalla que nuestra aplicacion
va a afrontar, para esto podemos encontrar varias soluciones... podriamos tener en cuenta
a nivel UX los dispositivos que queremos que funcione nuestra app y adaptar las vistas a
cada una de estas pantallas, aunque requeriria muchisima dedicacion ya que habria que 
calcular cada uno de los tamaños, podemos sino tambien tener una unica vista y adaptarla
de forma proporcional a cada una de las pantallas que la app detecte o podemos usar una libreria como react-native-responsive-screen. En este caso, esta fue mi eleccion ya que me va a ahorrar mucho tiempo de desarrollo. 

Para la navegacion del sitio voy a usar una libreria externa llamada react-native-navigation, ya que podremos tener una navegacion 100% nativa, a diferencia de otras librerias que lo manejan con javascript.

Para el testeo de la aplicacion voy a usar una libreria llamada Jest que viene configurada por defecto en el proyecto y tambien una libreria llamada Detox que nos permite hacer test e2e. 
Si me parece importante el testeo en el Front a pesar de que hay algunas tendencias que refieren que con solo testear el BackEnd ya seria una app confiable.
Me parece importante realizar un testeo de las funciones completas del Front y asi poder garantizar una app confiable y robusta, mas que nada si el equipo de desarrollo crece, es sumamente importante tener testing.

Ademas debemos tener cuidado con las animaciones en el sitio... Si bien son muy importantes para tener una mejor UX es importante tener cuidado con esto ya que muchas veces vamos a delegar performance por tener una transicion mas linda.

---------------------------------------------------------------------------------------------
- Que pediria a un equipo de desarrollo mobile a la hora de armar un equipo?

En la experiencia que tuve armando equipos de desarrollo me di cuenta la importancia de valorar las ganas y el compromiso de afrontar un nuevo desafio mas que ser un experto en una tecnologia especifica. Si me parece super importante obviamente que conozcan la herramienta y que sepan porque la usan y cuales son los pro y contras de usarla. Asi como tambien es importante que hayan tenido la experiencia de haber desarrollado alguna app ya que siempre surgen inconvenientes o cosas a tener en cuenta y eso forma parte de un gran aprendizaje.

Para React Native, me imporaria que sepan que librerias de manejo de estados existen... La historia de Flux, como nace Redux y tambien las alternativas de desarrollo que tienen en caso de no querer usarlas. Digamos, porque usar estas librerias y no solo usarlas porque la mayoria las usa. 

Tambien me parece un aspecto importante para el FrontEnd en general la vision de UX, ya que es sumamente importante poder entregar un producto funcional y no solo "lindo".

Aunque por sobre todas las cosas, valoro mucho mas a una persona con ganas de crecer, aprender y afrontar nuevos desafios mas que a un super experto de una tecnologia o libreria, al menos esa es mi apreciacion personal.
---------------------------------------------------------------------------------------------

Extra... Ultimamente las aplicaciones nuevas de React las estoy utilizando con una sintaxis funcional, ya que me esta resultando mas facil la legibilidad y mantenimiento del codigo.

Programando con clases lo realizaba de esta forma: 

class Avancargo extends Component {
  render() {
    return (<div>Hello Avancargo!</div>);
  }
}

Ahora suelo codearlo asi:

const Avancargo = () => <div>Hello Avancargo!</div>;

Pero esto es una apreciacion totalmente personal, lo que si es imporante unificar en un equipo de desarrollo el paradigma a utilizar ya que esto va a permitir el mayor entendimiento del mismo en el grupo.


