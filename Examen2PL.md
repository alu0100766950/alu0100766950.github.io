Procesadores de Lenguajes Examen 2
===

#Indice

* [JQuery](#jquery)
* [Ajax](#ajax)
* [Underscore](#underscore)
* [Local Storage](#local-storage)
* [Heroku](#heroku)
* [Analisis Lexico](#analisis-lexico)
* [Conceptos de Gramaticas](#conceptos-de-gramaticas)
* [Analisis Descendente Predictivo](#analisis-descendente-predictivo)
* [CoffeeScript](#coffeescript)
* [Jade](#jade)
* [MathJax](#mathjax)

#JQuery[:arrow_up:](#indice)

1. Falso
2. $
3. Todos los elementos div
4. Falso, solo usa HTML
5. $('p').css('background-color','red')
6. Todos los div con clase intro
7. hide
8. css
9. ajax
10. $('div').height(100)
11. $().ready
12. $().noConflict
13. $().toggle
14. Selecciona todos los descendientes (de clase head) de los div con id="intro".
15. No

#Ajax[:arrow_up:](#indice)

##Ajax 1

```
app.get(’/chuchu’, function (req, res) {
var isAjaxRequest = req.xhr;
...
}
```

##Ajax 2

Codigo JavaScript

* req.query
* Cuando el servidor responde y los datos llegan
* La respuesta del servidor
* El formato en que el cliente requiere las respuestas

#Underscore[:arrow_up:](#indice)

##Underscore 1
Argumentos:

* El template en forato string
* Los demas argumentos son opcionales. En caso de no pasarle mas argumentos, el template nos devolvera una funcion y ya mas tarde se instanciara. (Esto forma parte de la programacion funcional. **Mirar Haskell Curry**)
##Underscore 2
Diferencias:

* **<% ... %>** :arrow_right: Solamente evalua en JavaScript 
* **<%= ... %>** :arrow_right: Se evalua lo que esta dentro como codigo JavaScript y el resultado se interpola.
* **<%- ... %>** :arrow_right: Igual que el de arriba pero ademas se pasa un filtro para escapar los caracteres especiales que puedan interferir con el lenguaje HTML.

##Underscore 3
```
_.templateSettings = {
interpolate: /\{\{=.*?\}\}/gim,
evaluate: /\{\{.*?\}\}/gim
escape: /\{\{-.*?\}\}/gim
}
```

#Local Storage[:arrow_up:](#indice)
##Local Storage 1
La mejor forma de entender por qué es necesario el localStorage es indicando los tres grandes problemas de las cookies:

1. Espacio limitado: Una cookie sólo puede ocupar 4kb de espacio. Es por eso que las cookies suelen utilizarse sólo para almacenar un hash o un identificador que será utilizado por el servidor para identificar la visita.
2. Cada vez que se realiza una petición al servidor, toda la información que está almacenada en las cookies es enviada y también es recibida nuevamente con la respuesta del servidor. O sea, en los intercambios de información entre el navegador web y el servidor siempre van pegadas las cookies.

3. Las cookies tienen una caducidad.
Y aquí viene localStorage a solucionarlos la vida!

4. Espacio menos limitado: localStorage puede ocupar entre 5 y 10MB dependiendo del navegador web. Con 5 o 10 megas ya podemos tener algo más de información 

5. La información almacenada con localStorage no es enviada al servidor en cada petición.
No existe una caducidad para localStorage, la información quedará almacenada hasta que se elimine expresamente. Aunque se cierre el navegador.

Lo sé, una cookie tiene caducidad, pero le puedes poner que caduque dentro de 5 años… vale, sí… pero caduca, con localStorage nos olvidamos de tener que guardar la cookie aumentando el tiempo de caducidad.

##Local Storage 2
Sin embargo, que la información persista en el tiempo, no siempre es una buena idea. A veces lo que interesa es que la información se elimina una vez se cierre el navegador. Para estos casos, en vez de utilizar localStorage, se debe usar sessionStorage.

El sessionStorage es exactamente igual que localStorage, pero con la salvedad de que una vez cerrado el navegador se pierde la información, todo lo demás es lo mismo. Si se quiere trabajar con sessionStorage, sólo hay que coger todo el código de este artículo y donde pone localStorage cambiarlo por sessionStorage.

##Local Storage 3

1. Siguiendo estas reglas, un navegador web permite que scripts contenidos en una página acceda a datos en otra, pero sólo si ambas comparten el mismo origen. Un origen se define como la combinación del esquema URI, el nombre de dominio y número de puerto.
2. El acceso a los datos almacenados en el navegador, tales como los del localStorage, se encuentra separado por origen. Cada origen tiene su propio almacenamiento individual, y el JavaScript en un origen no puede leer o escribir en el espacio de otro origen.

##Local Storage 4
1. localStorage.setItem(‘chuchu’, chuchu)
2. var chuchu = localStorage.getItem(‘chuchu’)

##Local Storage 5
localStorage.removeItem(‘chuchu’)

#Heroku[:arrow_up:](#indice)

##Heroku 1
`heroku login`

##Heroku 2
`heroku create [<nombre>]`
`heroku`

##Heroku 3
`git push heroku master`

##Heroku 4
`git push heroku tutu:master`

##Heroku 5
`heroku open`
`<nombre>.herokuapp.com`

##Heroku 6
`heroku logs`

##Heroku 7
Procfile

##Heroku 8
package.json

##Heroku 9
Con foreman.
`foreman start`

#Analisis Lexico[:arrow_up:](#indice)
##Analisis Lexico 1

1. Comprueba que el último índice no casado por la regex sea igual al siguiente casado por la misma regex sobre str; es decir, que desde el lugar lastIndex hasta el primero que case en str, no hay ningún elemento. <br> En caso de ser así, devuelve m (el array del matching), y en caso contrario, null. <br> ***ES DECIR:*** <br> Teniendo en cuenta que se ejecute todo el tiempo sobre el mismo str, devuelve el matching en caso de que justo el elemento siguiente case, si hay **ALGO** que no case, devuelve null. <br>**cadena: tuntu <br> regex = /tu/g <br>tu index: 0 // con exec <br>tu index: 3<br>tu index: 0 // con bexec<br>null**

2. `null` <br> `[ “DBBD”, “BB”, “D”, index: 7, input: “dBdXXXXDBBD” ]`

##Analisis Lexico 2

* `var WHITES = /\s+/g;`
* `var ID = /[a-zA-Z_]\w*/g;`
* `var STRING = /('(\\.|[^'])*'|"(\\.|[^"])*")/g;`
* `var ONELINECOMMENT = /\/\/.*/g;`
* `var MULTIPLELINECOMMENT = /\/[*](.|\n)*?[*]\//g;`
* `var ONECHAROPERATORS = /([-+*\/=()&|;:,<>{}[\]])/g;`

#Conceptos de Gramaticas[:arrow_up:](#indice)
##Conceptos de Gramaticas 1
$V_{i+1} = \\{wv: w \in V_{i} \land v \in V\\}$

##Conceptos de Gramaticas 2
Cuádrupla $G = (N,T,S,P)$ donde:

* N es un conjunto finito de símbolos no terminales (variables).
* T es un conjunto finito de símbolos terminales (constantes), disjunto con N.
* S es un símbolo distinguido de N, el símbolo inicial.
* P es un conjunto finito de reglas de producción, cada una de la forma:

$(N \cup T)^\ast N(N \cup T)^\ast \to (N \cup T)^\ast$

##Conceptos de Gramaticas 3
Sea $G = (N,T,P,S)$ una gramática, y sean α, β, δ, φ, ρ, ... palabras de $\sum^\ast$ . Entonces:

* β se deriva de α en un paso de derivación, y lo denotamos con $α \Rightarrow β$ si existen dos cadenas $\Phi_1, \Phi_2 \in \sum^\ast$, y una producción δ → ρ tales que $α = \Phi_1 δ \Phi_2$ , y $β = \Phi_1 ρ \Phi_2$

* Notamos con $\Rightarrow^\ast$ al cierre reflexivo y transitivo de $\Rightarrow$. Es decir $α \Rightarrow^\ast β$ denota a una secuencia de derivaciones en un número finito de pasos desde α hasta β.

* $x \in \sum^\ast$ es una forma sentencial de $G$, si puede obtenerse la siguiente secuencia de derivaciones $S \Rightarrow^\ast x$ . En el caso particular de que $x \in T^\ast$ se dice que x es una sentencia

* Se denomina lenguaje formal generado por G al conjunto
$L(G) = \\{ x \in T^\ast | S \Rightarrow^\ast x\\}$

##Conceptos de Gramaticas 4
Según el tipo de Gramática se generará un lenguaje distinto:

* Lenguajes Recursivamente Enumerables:$P = \{ (u \to v) | u = xAy; u \in \sum^+; v,x,y \in \sum^\ast; A \in N\}$
* Lenguajes Dependientes del Contexto: $P = \\{ (S \to \lambda) o (xAy \to xvy) | v \in \sum^+ ; x,y \in \sum^\ast ; A \in N\\}$
* Lenguajes Independientes del Contexto:$P = \\{ (S \to \lambda) o (A \to v) | v \in \sum^+; A \in N\\}$
* Lenguajes Regulares:
	* Lineales por la derecha: $P = \\{ (S \to \lambda) o (A \to aB) o (A \to a) | a \in T; A,B \in N\\}$
	* Lineales por la izquierda: $P = \\{ (S \to \lambda) o (A \to Ba) o (A \to a) | a \in T; A,B \in N\\}$

##Conceptos de Gramaticas 5
Estructura jerárquica donde donde partiendo de la raíz, los hijos de cada nodo son posibles derivaciones de la gramática.

##Conceptos de Gramaticas 6
##Conceptos de Gramaticas 7
##Conceptos de Gramaticas 8
##Conceptos de Gramaticas 9

#Analisis Descendente Predictivo[:arrow_up:](#indice)

##ADP 1
```
expression = ->
	result = term()
	while lookahead and lookahead.type is "ADDOP"
		type = lookahead.value
		match "ADDOP"
		right = expression()
		result =
	    	type: "ADDOP"
	    	left: result
	    	right: right
	result
```

##ADP 2
```
statement = ->
	result = null
	if lookahead and lookahead.type is "ID"
  		left =
    		type: "ID"
    		value: lookahead.value
  		match "ID"
  		match "="
  		right = expression()
  		result =
    		type: "="
    		left: left
    		right: right
	else if lookahead and lookahead.type is "P"
		match "P"
  		right = expression()
  		result =
    		type: "P"
    		value: right
	else if lookahead and lookahead.type is "IF"
  		match "IF"
  		left = condition()
  		match "THEN"
  		right = statement()
  		result =
    		type: "IF"
    		left: left
    		right: right
	else # Error!
  		throw "Syntax Error. Expected identifier but found " +
    		(if lookahead then lookahead.value else "end of input") +
    		" near '#{input.substr(lookahead.from)}'"
	result
```

##ADP 3
```
condition = ->
    left = expression()
    type = lookahead.value
    match "COMPARISON"
    right = expression()
    result =
    	type: type
      	left: left
      	right: right
    	result
```

#CoffeeScript[:arrow_up:](#indice)

##Coffee 1
```
fact = (x) ->
	return 1 if x <= 1
	x * fact x - 1

alert fact(5)
```

##Coffee 2
```
container = "bucket"
liquid = "wine"
x = "Filling the #{container} with #{liquid}"
```

##Coffee 3
```
outer = 1
changeNumbers = ->
	inner = -1
	outer = 10
inner = changeNumbers()
```
**=**
```
var changeNumbers, inner, outer;

outer = 1;

changeNumbers = function() {
  var inner;
  inner = -1;
  return outer = 10;
};

inner = changeNumbers();
```
##Coffee 4
El (n...) significa que tendremos un numero aleatorio de argumentos que se almacenaran en un array. En este caso la funcion retornara un array con todos los argumentos que se le pasemos.
```
[1, 2, 3]
[[1, 2, 3]]
[1, 2, 3](... hace que se trate como distintos argumentos)
```


##Coffee 5
```
max is 10
ida is 9
tim is 11
```

```
((x)->x*x*x)(y) for y in [1..10] when y % 2 == 1
f = (x)->x*x*x
a = f(y) for y in [1..10] when y % 2 == 1
alert(a)
```
##Coffee 6
Funcion que suma los elementos del propio array. (:: se traduce como propotype). @reduce recibe como parametro una funcion y aplica esa funcion a los elementos del array.

```
Array::sum = -> @reduce ((a, b) -> a + b)
a = [1,2,3]
alert(a.sum()) // 6
```

#Jade[:arrow_up:](#indice)
##Jade 1
```
	#content
		.block
			input#bar.foo1.foo2
```

##Jade 2
Hace que se interprete todo lo que esta indentado en p como parrafo.

##Jade 3
* `li=name` crea un li con todos los caracteres especiales escapados.
* `li!=name` crea un li con los caraceteres especiales no escapados.

##Jade 4
El caso es el mismo que en el [Ejercicio 3](#jade-3) con # se escapan los caracteres especiales y con ! no se escapan.

##Jade 5
`input(type='text' placeholder='hola')`

#MathJax[:arrow_up:](#indice)

##MathJax 1
```
When $a \ne{} 0$ there are two solutions to $ax^2+bx+c=0$ and they are $ x ={ -b\pm \sqrt{b^2-4ac} \over 2a}$
```