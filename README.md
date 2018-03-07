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