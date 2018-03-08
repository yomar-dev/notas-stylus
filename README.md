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
Básicamente nos permiten reutilizar código ya que lo podemos agrupar en "función personalizada". <br>
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



[Documentación Stylus](http://stylus-lang.com/docs/)
