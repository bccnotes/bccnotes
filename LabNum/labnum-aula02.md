# Aula 02

### Obs : 

​	Os termos abaixo são definidos com base no experimento de observar as estrelas e tentar achar sua posição no céu.

***

## Modelagem

 - Escolha de modelos matemáticos / computacionais p/ representar o fenômeno observado
    - Exemplo : posição do sol
       - Podemos desenhar um eixo cartesiano e definir a posição do sol em relação ao eixo x ( L - O ) e ao eixo y (N - S)
       - Ou podemos desenhar um círculo com o zenite no meio, fazer um eixo azimutal.

## Discretização



- Aquisição dos dados em intervalos regulares
  - $s(t) \longrightarrow (s_0, s_1, s_2, .., )$
- Parametrização : Representar cada trecho de s(t) por um arco circunferência

***

## Algoritmo de solução

* Se o problema é encontrar eclipses do sol, então a partir das trajetórias $s(t)$ e $l(t)$ - respectivamente a trajetória do sol e da lua - queremos $t$ tal que :
  $$
  s(t) = l(t), \ ou \ seja\ (s(t) - l(t)) = 0
  $$

* Simplificando a busca dos trechos em que s(t) e l(t) estão definidos, poderíamos um algoritmo p/ encontrar zeros de funções.

***

## Acurácia 

* Expressar o erro numérico da solução (t que representa o momento do eclipse) em função de parâmetros do modelo (por exemplo o intervalo entre as observações)

***

## Eficiencia

* Poderia ser o nº Estimado de passos de Newton até atingir uma acurácia desejada. ou uma estimativa da taxa de convergência do algoritmo p/ a solução.
  * Ou seja, é o tempo necessário para o resultado do algoritmo convergir para um resultado aceitável tendo em vista o erro numérico desejado (ou seja, a acurácia).

***

## Robustez



* O valor procurado $t^*$ Deve ser > 0, s(t*) e l(t *) devem estar no hemisfério visível, não produza falhas de segmentação, divisões por zero.

***

## Erros

* Erro absoluto : 
  $$
  |u-v|
  $$



* Erro relativo : 
  $$
  \frac{|u-v|}{u}, u \neq 0
  $$
  Sendo u e v medidas escalares.



* Diferença básica entre eles : O erro relativo normatiza o erro em relação à grandeza das medidas (isso supondo que elas possuem uma ordem de grandeza similar). Eu posso ter u = 1 e v = 0.99, o erro absoluto vale 0.01, e o erro relativo 0.01; Agora, eu posso ter u = 100 e v = 99.99; Nesse caso, eu também tenho um erro absoluto de 0.01, mas o erro relativo vale 0.0001; Se olhassemos apenas para o erro relativo, avaliaríamos a acurácia das duas medidas como identicas, mas o erro relativo evidencia que a segunda medida foi muito mais acurata.

***

## Fórmula de Stirling



Implementação direta $O(n)$
$$
n! = \prod_{i = 1}^{n}i
$$
Podemos dar uma brincada
$$
ln(n!) = ln(\prod_{i = 1}^{n}i) = \sum_{i = 1}^nln(i) \approx \int_1^nln(x)\ dx
$$
Mas sabendo que 
$$
(x\cdot ln(x))' = ln(x) + 1
$$
Podemos integrar os dois lados e obter :


$$
\int_1 ^n ({x\cdot ln(x) }' = \int_1^nln(x) \ dx + \int_1^n1\ dx
$$
Resulta em
$$
n\cdot ln(n) - 1\cdot(ln(1)) = \int_1^nln(x) \ dx + n - 1
$$
Portanto
$$
\int_1^nln(x) \ dx = n\cdot ln(n) - n + 1
$$
Assim : 
$$
ln(n!) \approx n\cdot ln(n) - n + 1
$$
Aplicando o exponencial dos dois lados
$$
n! \approx e \cdot (\frac{n}{e}) ^ n
$$
Assim o custo se torna $O(log_2n)$.  Mas essa aproximação é uma subestimativa do valor do somatório na equação 2.  **A fórmula de Stirling mais completa por ser enunciada como : **
$$
n! \approx\sqrt{2\pi n}\cdot (\frac{n}{e}) ^n
$$

***

## Erros de truncamento / arredondamento

* Ex: 0.1 + 0.2 = 0.3? Não.
  * $(0.1)_{10}$ = 0.0001100110011...
  * $(0.2)_{10}$ = 0.0011001100110...
  * $(0.3)_{10}$ = 0.010011001...?
    * Eu começo pelo primeiro 00 porque sei que não vai produzir um "carry" pra esquerda
  * Nenhum desses números pode ser representado finitamente  na base decimal, mas o espaço de armazenamento para floats é arbitrário, então eu não represento o número inteiro, então a conta não vai dar certo na base decimal, pois a precisão da conta é finita.

### Obs : Glosario do octave

​	

* Uso de ; ao fim de statements  para suprimir o resultado de uma linha. A separação entre modo de script e interativo do octave é muito tênue, o ; faz essa separação.
* criação de array : n = 1:20; -> Cria uma matriz de uma linha e 20 colunas, e numera as colunas ja automaticamente (conferir isso)
* Posso multiplicar um array por escalar, funciona normal.
* .{OPERAÇÃO} : operação de radamar, É uma operação que envolve arrays
* .^ = Exponenciação de radamar : operador de exponencial que eleva todas casas do array.
* .* = Multiplicação de Radamar :  Multiplica dois arrays. Multiplica a primeira casa de um com a primeira do outro, a segunda com a segunda, etc etc...
* Indexa o array a partir do 1.