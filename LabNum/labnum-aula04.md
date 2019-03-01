# Aula 04

### Temas abordados : 

​	1) Exemplos de problemas estáveis ou não

​	2) Erros de arredondamento (página 14)



***



TODO : melhorar a compreensão do terceiro item do exemplo 1.5; É basicamente  que foi feito no livro (ver página 13 do livro)

***

### Exemplo 1.5

* Calcular a $\sqrt{}$ de um número próximo de 1 é um problema estável.

* *colocar foto da função raiz quadrada de x* 

  * Considere x_ (x-barra) = 1 e x = 1 + $\epsilon$. Note que 
    $$
    |f(x\_) - f(x)| = \sqrt{1+\epsilon} - 1
    $$

  * Para $\epsilon$ suficientemente pequeno, é razoável considerar que 
    $$
    f(x) \approx f(x\_) + \epsilon\cdot f'(x)\\ mas \ f(x\_) = f(x\_ + \epsilon) \ e \\ f(x\_) + \epsilon \cdot f'(X) = 1 + \epsilon \cdot \frac{1}{2}\cdot(1) ^\frac{-1}{2} = 1 + \frac{\epsilon}{2}
    $$

  * ASsim, para |$\epsilon$| << 1, temos : 

  * $$
    |f(x\_) - f(X)| \approx |1 - (1+\frac{\epsilon}{2})| = \frac{|\epsilon|}{2} = \frac{| x\_ - x|}{2}
    $$


***

### Outro exemplo : 

* Uma função contínua mal condicionada : 

* *colocar foto da função fx = tanx

* Se x e x* estão suficientemente próximos de $\frac{\pi}{2}$, com distância $\epsilon$ entre x e x*, então 
  $$
  f(x)-f(x*) \approx \epsilon \cdot f'(x*)
  $$

  * Obs : isso vem da definição de derivada. Epsilon é o mini incremento entre x e x*

* Logo, : 

$$
|tan(x) - tan(x*)| \approx \epsilon \cdot (\frac{sen(x)}{cos(x)})' = \epsilon \cdot (\frac{cos^2(x*) + sen^2(x*)}{cos^2(x*)})
$$





Logo : 
$$
|tan(x) - tan(x*)| = \frac{|x-x*|}{cos^2(x*)}, mas \ cos(x*) \approx 0 \ p/ \ x* \approx \frac{\pi}{2}
$$
Podemos concluir, assim, que uma diferença pequena entre x e x barra acarreta numa diferença enorme entre f(X) e f(x*) nesse caso

***

### Exemplo 1.6

* Estime numericamente os valores : 
  $$
  y_n = \int^1_0 \frac{x^n}{x+10}dx
  $$
  Para n = 0, ... , 30

* Observe que : 
  $$
  \int^1_0 \frac{(x+10)\cdot x^{n-1}}{x+10}dx =  \int^1_0 x^{n-1}dx
  $$

* Podemos reescrever os dois lados da equação como : 
  $$
  \int^1_0 (\frac{x^n}{x+10} + \frac{10\cdot x^{n-1}}{x+10}dx  = \frac{1}{n} - 0
  $$


* Mas sabendo que 
  $$
  y_n = \int^1_0 \frac{x^n}{x+10}dx
  $$


* Assim, temos  : 
  $$
  y_n + 10y_{n-1} = \frac{1}{n}
  $$

* Isso sugere o método :  
  $$
  \begin{array}{22} y_0 = \int^1_0 \frac{x^0}{x+10}dx \ resolver\ na\ mão \\
  y_n = \frac{1}{n} - 10y_{n-1}, \forall n>0 \end{array}
  $$
  Para n > 0, isso sugere o cálculo de $y_0$ e posteriormente vou calculando num algoritmo.

* Esse método é matematicamente exato, mas ocorrem erros de arredondamento.

  A Expressão $y_n = \frac{1}{n} - 10y_{n-1}$ exibe a característica de crescimento exponencial dos erros de arredondamento (a cada iteração, o erro é multiplicado por 10 - ver página 14 do livro).

***

## Representação em ponto flutuante

Considere $x \mathbb{E} \mathbb{R}$ genérico : 
$$
x = +_- d_!.d_2d_3d_4... \times 10 ^k, d_i = mantissa
$$
O pc representa como : 
$$
x = +_- D_1.D_2D_3D_4...D_t \times 10 ^K, t = precisão \ finita
$$
A idéia é comparar o 1º Dígito não armazenável ($d_{k+1}$) com o erro de arredondamento pretendido, nesse caso  : 
$$
\frac{1}{2} \times10^{-(t-1)}
$$
O que isso significa? t é a precisão do meu computador, eu pego metade do ultimo digito armazenavel (seria um 0.00005, algo assim).

***

### Em base 2

​	Qualquer $x \mathbb{E} \mathbb{R}$  pode ser escrito como : 
$$
x = 1.d_1d_2d_3...\times2 ^ k
$$

$$
flt(x) = 1.D_1D_2D_3...D_t \times 2 ^K
$$

​	Exemplo : 
$$
1.1010|111...
$$
​		Representado com t = 4 como 1.1010