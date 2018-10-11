---
layout: post
title: What does the fox say?
---

What does the fox say es un programa  que resolví en [COJ](http://coj.uci.cu/24h/problem.xhtml?pid=2995) de la categoría **strings**, el problema es el siguiente...

### Description 
Determined to discover the ancient mystery – the sound that the fox makes – you went into the forest, armed with a very good digital audio recorder. The forest is, however, full of animals’ voices, and on your recording, many different sounds can be heard. But you are well prepared for your task: you know exactly all the sounds which other animals make. Therefore the rest of the recording – all the unidentified noises – must have been made by the fox.

### Input specification
The first line of input contains the number of test cases T . The descriptions of the test cases follow:
The first line of each test case contains the recording – words over lower case English alphabet, separated by spaces. Each contains at most 100 letters and there are no more than 100 words. The next few lines are your pre-gathered information about other animals, in the format **animal goes sound.** There are no more than 100 animals, their names are not longer than 100 letters each and are actual names of animals in English. There is no **fox goes** ... among these lines.
The last line of the test case is exactly the question you are supposed to answer: what does the fox say?
### Output specification
For each test case, output one line containing the sounds made by the fox, in the order from the recording. You may assume that the fox was not silent (contrary to popular belief, foxes do not communicate by Morse code).
### Sample input
1  
toot woof wa ow ow ow pa blub blub pa toot pa blub pa pa ow pow toot  
dog goes woof  
fish goes blub  
elephant goes toot  
seal goes ow  
what does the fox say?  
### Sample output
wa pa pa pa pa pa pow  

>Leyendo el problema no podemos dar cuenta que lo que tenemos que hacer comparar la cadena donde están todos los sonidos e ir eliminando los sonidos de las cadenas siguientes.



```cpp
int main(){
	char palabras[102][100];
	int t, cont=0, rep=0, cont2=0;
	char sounds[100][100];
	char basura[100];
	char basura2[100];
	scanf("%d", &t);
	while(rep < t){
		cont = 0; cont2=0;
	while(1){
		scanf("%s", &palabras[cont]);
		if( strcmp( "goes", palabras[cont])==0 ){
			break;
		}
		cont++;
	}
	while(1){
		scanf("%s %s %s", &sounds[cont2], basura, basura2);
		cont2++;
		if( strcmp("what", basura)==0 ){
			scanf("%s %s", basura, basura2);
			scanf("%s", basura);
			break;
		}
	}
	int paso=0;
	for(int i=0; i<cont-1; i++){
		paso = 0;
		for(int j=0; j<cont2; j++){
			if( strcmp(palabras[i], sounds[j])==0 ){
				paso=1;
				break;
			}
		}
		if(paso==0){
			printf("%s ", palabras[i]);
		}
	}
	printf("\n");
	memset(palabras, 0, sizeof(palabras[0][0]) * 100 * 102);
	memset(sounds, 0, sizeof(sounds[0][0]) * 100 * 100);
	memset(basura, 0, sizeof(basura));
	memset(basura2, 0, sizeof(basura2));

	rep++;
} 
	return 0;
}
```