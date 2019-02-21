# Aula 01



## Informações da disciplina : 

​	Prof.: Marcelo Queiroz

​	**Site**: www.ime.usp.br/~mqz

​	**Contato** : mqz@ime.usp.br

​	**Bibliografia** : A first Course in Numerical Methods, Ascher & Greifs, 2011; Caps 1,2,3,10,11,14,15.

​	**Provas**: P1: 22/04, P2: 29/05, P3: 26/6; No caso de perder uma prova por motivo justificável, a média vai ser resolvida indivuldalmente com o professor

​	**EPs**: Vários ep's pequenos

​	**Medias** : MP = $\frac{P1+2\cdot P2+2 \cdot P3}{5}$ Mep = Média simples, MF = $\frac{3\cdot MP + MEP}{4}$, se MP >= 5 && MEP >= 5; Do contrário, MF = min{MP,MEP}.

​	**Linguagem**: Octave

***

## Cap 1 : Algoritmos Numéricos e computação Científica (O que será visto)

 - Erros de aproximação e arrendondamento : Quando tratamos de algoritmos tradicionais, analisamos sua complexidade baseado em tempo médio de execução ou memória média utilizada. Com algoritmos Numéricos, podemos avaliar a qualidade de Algoritmos Numéricos por meio de erros de aproximação e arrendondamento.
- **Acurácia, eficiência e robustez** : **Acurácia** determina a qualidade da solução em função dos seus dados. **Eficiência** está relacionada inversamente à complexidade computacional exigida pra rodar o algoritmo, nessa disciplina, está muito relacionado ao tempo necessário para que o Erro numérico se torne arbitrariamente pequeno. **Robustez** é uma característica que está relacionada à preparação do algoritmo para lidar com ~corner cases : se o algoritmo lida bem com divisão por zero, numeros positivos, negativos, etc etc... ele é robusto.
- **Condicionamento do problema e estabilidade do algoritmo**: 
- **Medidas como O(...) e $\theta$(...) para avaliar Eficiência e acurácia**

***

## Cap 2 : Aritmética do ponto flutuante e erro de arredondamento

* **Representação (simples/dupla, espaçamento)**
* **Acumulação de erros**
* **Padrão IEEE 1985 -> 2008 **

***

## Cap 3 : Equações não lineares em 1 var.  Encontrar x tal que f(x) = 0

* **Metódo da Bisseção** : procura um ponto positivo da função, um negativo da função, usamos a propriedade de continuidade para achar a raiz no meio do intervalo
* **Método do ponto fixo** : encontra x tal que g(x) = x. Se definirmos g(x) = f(x) - x, dessa forma podemos encontrar f(x) = 0
* **Método de Newton**
* **Otimização de funções de 1 variável**

***

## Cap 10 : Interpolação polinomial 

* Encontrar modelos polinomiais p/ funções + gerais : Ajuste a dados mensurados, aproximação de funções
* **Predição** : interpolação/extrapolação
* **manipulações** : Diferenciação/integração
* **INterpolação** : Polinomial, lagrange, newton.

***

## Cap 14 : Diferenciação Numérica 

 * **Dado f(x), calcular f'(x)**
 * Taylor
 * Aproximação c/ 2 pontos, 3 pontos, 5 pontos

***

## Cap 15 : Integração Numérica

 * Aproximação trapezoidal, Simpson, Ponto médio
 * Aproxiações de f(x) por polinômios