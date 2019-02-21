# Funções Diferenciáveis e Séries - Aula 01



## Professora :  Leila Maria Vasconcelos - Sala 105, Bloco A

###  Site da disciplina : www.ime.usp.br/~leila

***Bibliografia*** :

 * Um curso de Cálculo, vol. 2, James Stewart
 * Cálculo com Geometria Analítica, Simmons

## Datas de Provas : 

* P1 : 22/04
* P2 : 17/06
* PSub ( aberta ) : 24/06
* Média : $\frac{P1+P2}{2}$

***

## Aula 01 - Introdução às Séries

**Definição de Sequência de Números Reais** : 

​	Def : Uma sequência é uma *função* do tipo $ f : \mathbb{R}^* \rightarrow \mathbb{N}  $, e denotamos $a_n = f(n)$, 		 como a sequência até um n arbitrario. Notação alternativa : $a_n = (a_n) $

### Ex 1 : 

​	Descubra a lei da sequência : $0 , \frac{1}{2}, 0, \frac{1}{3}, 0 ...$

​						$$f(n) = \begin{array}{11} 0, se\  n\  for\ par\\ \frac{1}{k+1} se\ n = 2k+1\end{array} $$

***



### Definição :

​	Seja ($a_n$) uma sequência de números reais. Dizemos que $a_n \rightarrow L \ \mathbb{E}\ \mathbb{R}$ ou $\ lim_{n\rightarrow \infty} a_n = L$

​	se os $a_n$ ficam arbitrariamente próximos de L para n suficientemente grandes

​		Em outras palavras : A sequência converge se o limite tendendo ao infinito existe.



***



### Teorema 1 : 


$$
lim_{x \rightarrow \infty} \ f(x) = L \rightarrow lim_{n \rightarrow \infty} f(n) = L, \ x \mathbb{E} \mathbb{R}, n\mathbb{E}\mathbb{N}
$$


​		Ou seja : Se o limite existe para uma função **Real**, ele também é valido no intervalo dos naturais. Isso nos permite realizar manipulações algébricas como L'Hospital em limites de intervalos Naturais, nos quais não seria possível derivar pois funções Naturais não são contínuas.



**Aplicação** : 
$$
lim_{n\rightarrow\infty} \frac{ln(n)}{n}
$$
​	Aplicando o teorema 1, temos : 
$$
lim_{x\rightarrow\infty} \frac{ln(x)}{x}
$$
​	O que é uma indeterminação do tipo $\frac{\infty}{\infty}$, então podemos aplicar L'Hospital...
$$
lim_{n\rightarrow\infty} \frac{\frac{1}{x}}{1} = 0
$$
​	Portanto, podemos concluir que : 
$$
lim_{n\rightarrow\infty} \frac{ln(n)}{n} = 0
$$
​	E a série converge.



**Importante** : A recíproca ***NÃO*** é verdadeira. Se uma série converge no infinito não implica que o limite exista nos Reais. Exemplo : 
$$
lim_{n\rightarrow\infty}sen(\pi\cdot n)
$$
O limite existe e vale 0, mas se aplicarmos o teorema 1 ao contrário : 
$$
lim_{x\rightarrow\infty}sen(\pi\cdot x)
$$
Note que o limite não existe, já que x é um valor real e faz o valor do seno oscilar e nunca convergir para um valor.



### Propriedas dos limites de Série : 

​	As mesmas propriedades de limites reais : 

 * Limite da soma : soma dos limites.
 * Limite do produto : produto dos limites.
 * Limite da subtração : subtração dos limites.
 * Limite da divisão : divisão dos limites.

​	













​			 

