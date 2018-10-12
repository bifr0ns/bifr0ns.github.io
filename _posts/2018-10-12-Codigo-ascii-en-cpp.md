---
layout: post
title: Código ASCII en C++
---

El código ASCII puede ayudar a resolver varios problemas sobre caracteres que se tengan dentro la programación, en este ejemplo resolveré un problema usando el código ASCII. 

El código ASCII es una estandarización para el alfabeto y los caracteres que vemos en nuestro teclado. A cada letra o símbolo se le da un número. Por ejemplo _@_  tiene el número _64_, y podríamos sacar la _@_ pulsando _alt+64_.

El problema a resolver es el siguiente:

### Coco-Bits and the Coco-Strings 
No tiene nada que ver con mamá Coco!

### Description
The Coco-Bits are fans of Coco-Strings. Coco-Strings have opposite sisters they have never met, Inverse-Coco-Strings. An Inverse-Coco-String is a Coco-String where all characters are opposed, regarding size, to its twin Coco-String sister.

The Coco-Bits want you to help them find their opposite sisters.

### Input specification
A line representing the amount of Coco-Strings (1 <= CC <= 100). Each following line contains a Coco-String.

### Output specification
The corresponding Inverse-Coco-String.

### Sample input
3  
a  
BcD  
FeeU  

### Sample output
A  
bCd  
fEEu  

>El problema nos dice que debemos invertir entre minúsculas y mayúsculas las letras!

Y el código ASCII cómo nos puede ayudar en esto te preguntas? Bueno, observando los valores de las letras mayúsculas y minúsculas en el código ASCII podemos observar que las letras mayúsculas se encuentran en el **rango 65 a 90**, mientras que las letras minúsculas se encuentran en el **rango 97 a 122**.

![codigo ascii](/images/codigo-ascii-cpp/codigo-ascii.jpg)

Entonces cada código ASCII que sea mayor que 96 será una letra minúscula, y cada código ASCII mayor que 64 pero menor que 97 será una letra mayúscula. Hasta aquí tenemos una parte del problema. Ahora sólo tenemos que invertir las letras, y para poder hacer esto recurrimos al código ASCII de nuevo. 

Si la _A_ mayúscula es _65_ y la _a_ minúscula es _97_, eso significa que hay una diferencia de 32 caracteres entre cada una, así que lo único que tenemos que hacer es sumar o restar 32 dependiendo de qué letra sea. Si nuestra letra es _R_ cuyo número es _82_ tendríamos que sumarle 32 para tener el código _114_ que es la _r_.

El código para resolver el problema es el siguiente, va después de las variables declaradas para leer el número de cadenas que tendrá el problema. 

```cpp
for(int k=0; k<n; k++){
		cin >> str;
		for(int i=0; i < str.length(); i++){
			if(str[i] > 96){
				c = (str[i]-32);
				cout << c;
			}
			else if(str[i] > 64){
				c = (str[i]+32);
				cout << c;
			}
			else
				cout << str[i];
		}
		cout << "\n";
	}
```

Donde pasaremos por cada letra de cada cadena y compararemos si su código ASCII es mayor a 96 (letra minúscula) y le restaremos 32 para hacerla mayúscula, y si no, mientras sea mayor a 64 (letra mayúscula) le sumaremos 32 para convertirla a minúscula!