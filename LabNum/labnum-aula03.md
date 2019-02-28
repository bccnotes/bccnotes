# Aula 03



***

## Na aula passada : 

* **Fontes de Erros** : 

  * Erros no problema : 
    * Erros no modelo.
    * Erros de aquisição.
  * Erros de aproximação : 
    * Erros de discretização.
    * Erros de Convergência.
  * Erros de representação (truncamento) : 
    * São os erros relativos à representação com ponto flutuante.
    * Erros relativos às operações numéricas

  ***

  ## Erros de Aproximação : 

  ## 					Séries de Taylor

* Considere $f : \mathbb{R} \rightarrow \mathbb{R} \ e^\infty$. Então existem coeficientes $a_0, a_1, a_2, ...$ tais que 
  $$
  f(x) = \sum_{k=0}^{\infty}{a_k\cdot x^k}
  $$
  Calculando f(x), f'(x), f''(x), ... em x = 0, obtemos : 
  $$
  f(0) = a_0
  $$
  e
  $$
  f'(0) = \sum_{k=1}^{\infty}{k\cdot a_k \cdot x^{k-1}} = a_1
  $$
  Podemos ir adiante para a segunda derivada ...
  $$
  f''(0) = \sum_{k=2}^{\infty}{k\cdot a_k \cdot x^{k-2}} = 2\cdot a_2
  $$


  Para a terceira derivada (já vai dar pra ver o padrão) : 
  $$
  f^3(0)\sum_{k=3}^{\infty}{k\cdot a_k \cdot x^{k-3}} = 3!\cdot a_3
  $$
  Por indução, podemos provar que : 
  $$
  f^n(x) = \sum_{k=n}^{\infty}{k\cdot a_k \cdot x^{k-n}} = n! \cdot a_n \longrightarrow a_n  = \frac{f^{(n)}(0)}{n!}
  $$
  Então a fórmula de taylor pode ser descrita como : 
  $$
  f(x) = \sum_{k=0}^{\infty}{a_k\cdot x^k}, \ a_k  = \frac{f^{(k)}(0)}{k!}
  $$
  Dado $x_0\mathbb{E} \mathbb{R}$
  $$
  g(x_0 + h) =  f(h) = \sum_{n=0}^{\infty}{\frac{f^{(n)}(0)\cdot h^n}{n!}} = \sum_{n=0}^{\infty}{\frac{g^{(n)}(x_0)\cdot h^n}{n!}}
  $$

  ***

* Exemplo : Cálculo de $f(x_0)$ usando a aproximação de taylor

$$
f'(x_0) = \frac{f(x_0) - f(x_0 + h) + \frac{h^2}{2}f''(x_0)+\frac{h^3}{3!}...}{-h}
$$

O que equivale a 
$$
\frac{f(x_0+h)-f(x_0)}{h} - \frac{hf''(x_0)}{2} - \frac{h^2f''(x_0)}{3!}
$$


Assim : 
$$
f'(x_0) - f''(x_0) = E(x) = \frac{hf''(x_0)}{2} + \frac{h^2f''(x_0)}{3!}
$$
