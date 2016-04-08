# 8.abril.2016
función Acf (autocorrelacion) y detalles del examen

## 8 de abril de 2016 ##

## DETALLES DEL EXAMEN

## el examen seria en dos partes:
## parte 1: generar un script en la computadora
## parte 2: el profesro da un script ya hecho y el nos indica que lineas hay que 
##          explicar y añadir comentarios (en una hoja)

### estructura del examen ###

# 1) manejo de base de datos en R
#    expprtar bases, etiquetar, generar una base de datos, recodificar, seleccionar
#    casos, graficar (histogramas, etc)
# 2) series de tiempo en R
#    declarar una serie de tiempo, dividir una serie de tiempo, graficar st,
#    interpretar graficas on estacionalidad, tendencia y ciclo
# 2.1) como determinar estacinalidad en una serie de tiempo con la funcion de 
#      autocorrelacion, calculo de correlacion y covarianza



## funcion de autocorrelacion!!!

# la autocorrelacion mide la correlacion entre dos variales
# separadas por k periodos
# propiedades de la autocorrelacion:
# P0 = 1
# -1 <= P0 <= 1
# SIMETRIA Pj = Pj-1 (autocorrelacion en el tiempo j)

install.packages ("fpp")
require (fpp)
Acf(beer) ## funcion para conocer la autocorrelacion de los datos
xx <- Acf (beer, main= "ACF of quarterly beer production")
Acf(beer, main= "ACF of quarterly beer production")
## las dos ultimas lineas hacen lo mismo
## observando la grafica 
## cuando existes datos positivos altos es muyn probable que exusta estacionalidad
## 
lag(xx) ##v es como para observar las coordenadas o los puntos de la grafica
names (xx) ## para observar los nombres que stan dentro de xx
xx$acf ## señeccionamos solo acf de nuestra base xx

## la grafica que genera el acf se le donomina correlograma y permite identificar 
## la correlacion

## ejercicio:

netflix <- read.csv("C:\\Users\\SALA-C9\\Desktop\\netflix.csv", header = TRUE)
STnetflix <- ts(netflix[,5], start = 2015, frequency = 12) ## los corchetes señalan 
## con que columna queremos trabajar
STnetflix
plot.ts(STnetflix)
plot(STnetflix)
## la grafica queda igual
Acf(STnetflix)
x <- Acf (STnetflix, main= "ACF de los precios de cierre de NetFlix")
## a grandes rasgos pode4mos ver que no hay estacionalidad a pesar de que se dispara 
## un punto pero todos los demas estan dentro del rango, con esta serie de tiempo si 
## se puede trabajar, si tubiera muchos datos fuera del rago tendriamos que arregar
## la serie de tiempo para poder trabajar con ella
x$acf ## para observar los puntos de acf
