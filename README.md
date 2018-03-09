# Notas Stylus #

### Variables ###
Crear variables es muy sencillo, simplemente hay que darle un nombre y un valor. <br><br>
**Ejemplos:** <br>
`font-size-normal = 16px` <br>
`font-size-small = 14px` <br>

Además también podemos realizar operaciones con dichas variables <br>
**Ejemplo:** `padding: font-size-normal - font-size-small`


### Importar archivos ###
Para importar archivos utilizamos la palabra reservada **@import**. <br>
**Ejemplo:** `@import "_variables.styl"`, de esta forma estaria importando el archivo **_\_variables.styl_** en el cual se encuentran todas las variables.


### Organizar archivos ###
Una buena practica es módularizar y tener todo separado y organizado, podriamos tomar como ejemplo la siguiente estructura de archivos y carpetas: <br>
~~~
@import "lib/_variables.styl"
@import "lib/_mixins.styl"
@import "lib/_functions.styl"

@import "layout/_site.styl"
@import "layout/_blocks.styl"

@import "base/_links.styl"
@import "base/_buttons.styl"
@import "base/_typography.styl"
@import "base/_tables.styl"

@import "components/_grid.styl"
@import "components/_utilities.styl"
~~~


### Mixins ###
Básicamente nos permiten reutilizar código ya que lo podemos agrupar en una "función personalizada". <br>
**Ejemplo:** <br>
~~~
mixin-max-width()
	width: 800px
	margin: 0 auto;


.section
	mixin-max-width()

.article
	mixin-max-width()
~~~

<br>El resultado final seria el siguiente: <br>
~~~
.section {
  width: 800px;
  margin: 0 auto;
}

.article {
  width: 800px;
  margin: 0 auto;
}
~~~


### Mixins Paramétricos ###
Este tipo de mixins puede recibir paramétros que luego van a ser remplazados por los varoles que se le indiquen. <br>
**Ejemplo:** <br>
~~~
mixin-min-width(width)
	min-width: width
	padding: 4em 0


.hero
	mixin-min-width(90%)
~~~

<br>El resultado final seria el siguiente: <br>
~~~
.hero {
  min-width: 90%;
  padding: 4em 0;
}
~~~

<br>También podemos utilizar valores por defecto que se asignaran en caso que no se especifiquen por parametro al momento de llamar al mixin. <br>
**Ejemplo:** <br>
~~~
max-width-landing = 1024px

mixin-min-width-landing(width = max-width-landing)
	min-width: width
	padding: 2em 0


.landing
	mixin-min-width-landing()
~~~

<br>El resultado final seria el siguiente: <br>
~~~
.landing {
  min-width: 1024px;
  padding: 2em 0;
}
~~~


### Condicionales ###
**Ejemplo:** <br>
~~~
box(x, y, margin-only = true)
	if margin-only
		margin: x y
	else
		padding: x y

tono(dark = true)
	if dark
		color: #fff
		background: #000
	else
		color: #000
		background: #fff
		

.div
	box(10px, 15px)
	tono()
	
.article
	box(10px, 15px, false)
	tono(false)
~~~

<br>Resultado: <br>
~~~
.div {
  margin: 10px 15px;
  color: #fff;
  background: #000;
}

.article {
  padding: 10px 15px;
  color: #000;
  background: #fff;
}
~~~


### Directiva FOR ###
Esta directiva nos permite realizar ciclos para realizar un determinado número de veces. <br>
**Ejemplo:** <br>
~~~
grid-size = (1..12)

.grid
	display: flex
	flex-wrap: wrap
	position: relative
	flex-direction: row
	
[class^="grid--item"]
	flex-shrink: 0
	margin-right: 0
	flex-grow: 1
	
for i in grid-size
	.grid--item-{i}
		width: (100 / i) * 1%
~~~

<br>Resultado:<br>
~~~
.grid {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -ms-flex-wrap: wrap;
  flex-wrap: wrap;
  position: relative;
  -webkit-box-orient: horizontal;
  -webkit-box-direction: normal;
  -ms-flex-direction: row;
  flex-direction: row;
}

[class^="grid--item"] {
  -ms-flex-negative: 0;
  flex-shrink: 0;
  margin-right: 0;
  -webkit-box-flex: 1;
  -ms-flex-positive: 1;
  flex-grow: 1;
}

.grid--item-1 {
  width: 100%;
}

.grid--item-2 {
  width: 50%;
}

.grid--item-3 {
  width: 33.333333333333336%;
}

.grid--item-4 {
  width: 25%;
}

.grid--item-5 {
  width: 20%;
}

.grid--item-6 {
  width: 16.666666666666668%;
}

.grid--item-7 {
  width: 14.285714285714286%;
}

.grid--item-8 {
  width: 12.5%;
}

.grid--item-9 {
  width: 11.11111111111111%;
}

.grid--item-10 {
  width: 10%;
}

.grid--item-11 {
  width: 9.090909090909092%;
}

.grid--item-12 {
  width: 8.333333333333334%;
}
~~~

[Documentación Stylus](http://stylus-lang.com/docs/)
