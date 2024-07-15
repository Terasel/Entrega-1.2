Builder es un patrón de diseño creacional, lo que significa que proporciona una forma de crear objetos para mejorar la flexibilidad y la capacidad de reutilizar el código existente. 
Más concretamente, Builder es un patrón la idea del cual es la creación de objetos complejos paso a paso con características diferentes pero una estructura parecida usando el mismo código para construirlos. 

Imaginemos que estamos trabajando en una aplicación para la entrega de pizzas a domicilio desde donde podemos pedir una de las que tienen en un catálogo o pedir una que tenga los ingredientes que queramos. 
Evidentemente, podemos pedir la pizza más sencilla que tengan, solo con tomate, mozzarella y albahaca. Pero qué pasa si queremos una pizza que sea más compleja, como por ejemplo una cuatro quesos? Hay dos opciones: 

Primero, se puede extender la clase base “Pizza” y crear subclases hasta que estén representadas todas las combinaciones posibles. 
Pero no hacen falta muchos conocimientos de matemáticas para deducir que de esta forma se puede acabar teniendo una cantidad enorme de subclases, la cual pude subir aún más si en algun momento se amplia la variedad de ingredientes disponible.

Segundo, se puede crear un constructor gigante dentro de “Pizza” que contenga todos los parámetros (ingredientes) posibles que se puedan poner en la pizza. 
Pero en este caso la mayoría de llamadas al constructor estarán formadas mayoritariamente por código inútil que no se usa. No todas las pizzas van a llevar setas, por lo que el parámetro “Setas” va a estar vacío la mayoría de las veces.

Cómo solucionar este problema? Con el patrón Builder. Éste se basa en el concepto de sacar la construcción del objeto de la propia clase del objeto y colocarla en objetos independientes (constructores), 
los cuales se organizan en una serie de pasos a ejecutar. Es importante especificar que no hace falta ejecutar todos y cada uno de los posibles pasos para generar el objeto (esto es precisamente la razón de ser de Builder). 
De esta forma se pueden construir objetos con diferentes cantidades de pasos de construcción, o con el mismo número de pasos pero diferentes, usando sólo la cantidad de código estrictamente necesaria según el caso. 
Por ejemplo, podemos pedir dos pizzas con cuatro ingredientes cada una, ejecutar el mismo número de pasos de construcción, y acabar teniendo dos pizzas completamente diferentes, una con tomate, mozzarella, atún y salmón 
y otra con tomate, queso brie, jamón serrano y rúcula. Sin embargo, esto sólo funcionaría si el código cliente que invoca los pasos de construcción es capaz de interactuar con los constructores mediante una interfaz común. 

Se puede dar un paso más y crear una clase directora independiente que contenga una serie de llamadas predeterminadas a los pasos de construcción, con un orden y cantidad de pasos ya establecidos. 
Técnicamente este paso no es necesario ya que desde el código cliente ya se puede llamar a los constructores, pero este tipo de clase puede ser útil si hay una serie de llamadas con pasos concretos que sean de uso particularmente común. 
Por ejemplo, en esta clase se podrían guardar las configuraciones con las que el cliente pueda pedir las pizzas del catálogo ya que éstas vienen definidas de antemano.

Para recapitular, Builder es un patrón de diseño las ventajas del cual son la construcción paso a paso del objeto, la capacidad de aplazar pasos o ejecutarlos recursivamente, 
la capacidad de reutilizar código para construir productos diferentes y la capacidad de aislar un código de construcción complejo de la lógica de negocio del producto. 
La desventaja de este patrón es que puede hacer que el código sea más complejo.

Para ver un ejemplo sobre la estructura del código de un fichero donde se aplique este patrón de diseño, consultar el fichero “EjemploBuilder.ts”.
