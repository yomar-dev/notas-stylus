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