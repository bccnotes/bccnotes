# Representação em Ponto Flutuante

Img de bits de um float

Bits são divididos em:

- 1 bit para o sinal ($\sigma$)
- Expoente ($exp​$)
- Mantissa ($d_1,d_2,...d_t$)

$$
fl(x) = \sigma.(d_1d_2d_3...d_t)\times \beta^{exp}\\
d_1 \in \{1,..,\beta-1\} \\
d_i \in \{0,..,\beta-1\} \quad i\geq 2 \\
exp \in \{L,...,U\}
$$

​	Aonde a base é $\beta = 2$, $L$ é o menor expoente possível, e $U$ o menor possível.

## Precisão da Máquina (Unidade de arredondamento)

$$
fl(x) = \sigma . \bigg( \sum_{i=1}^t d_i \times \beta^{1-i} \bigg)\beta^{exp}
$$

​	Temos que: $\eta = \frac{1}{2} . \beta^{1-t}$ é o maior erro possível cometido por arredondamento, enquanto $2\eta$ é a menor variação possível entre 2 números de ponto flutuante.

### Ex de Arredondamento:

​	Temos $x = 1.41421359...$ , o arredondamento é feito da seguinte maneira:
$$
\text{se }d_{t+1} < \frac{\beta}{2} \quad \rightarrow\quad  \text{arredondamento para baixo } (f_i =d_i) \\
\text{se }d_{t+1} > \frac{\beta}{2} \quad \rightarrow\quad  \text{arredondamento para cima } (f_1f_2...f_t =d_1d_2...d_t + \beta^{1-t}) \\
\text{se }d_{t+1} = \frac{\beta}{2} \quad \rightarrow\quad  \text{arredondamento depende de }d_{t+1},d_{t+2}...
$$
​	Obs: se $d_t = \frac{\beta}{2}$ e $d_i = 0, i>t$ arredondamos para o número par mais próximo.	
$$
0,99995001 \rightarrow 1,0000000 \\
0,99985001 \rightarrow 0,9998000
$$

## Truncamento

$$
x = \pm (d_1d_2d_3...d_td_{t+1}...) \rightarrow fl(x) = \sigma(d_1d_2...d_t)\beta^{exp}
$$



Obs: $\beta^{1-t}$ é  realmente a menor variação entre dois valores adjacentes? 

|         $x$          |         $y$          |     $|x-y|$      | $\frac{|x-y|}{|x|}$ |
| :------------------: | :------------------: | :--------------: | :-----------------: |
|       $1.000$        |       $1.001$        |     $0.001$      |       $0.001$       |
| $1.000\times10^{97}$ | $1.001\times10^{97}$ | $1\times10^{97}$ |       $0.001$       |

## 

## Teorema do Erro de Representação do Ponto Flutuante

​	Seja $x \rightarrow fl(x) = g \times \beta^e$, aonde $x\neq0$ e $g$ é a mantissa normalizada com sinal. 
​	Então o erro absoluto cometido ao se usar a representação em ponto flutuante é limitado por:
$$
|x-fl(x)| \leq 
\begin{cases} 
	\beta^{1-t}.\beta^e & \text{,para truncamento.} \\
    \frac{1}{2}\beta^{1-t}.\beta^e & \text{,para arredondamento.}
\end{cases}
$$
​	Enquanto o erro relativo satisfaz
$$
\frac{|x-fl(x)|}{|x|} \leq 
\begin{cases} 
	\beta^{1-t} & \text{,para truncamento.} \\
    \frac{1}{2}\beta^{1-t} & \text{,para arredondamento.}
\end{cases}
$$


## Operações

​	O erro nas operações é:
$$
fl(fl(x)\pm fl(y)) = (fl(x) \pm fl(y))(1+\epsilon_1) \\
fl(fl(x)\times fl(y)) = (fl(x) \times fl(y))(1+\epsilon_2) \\
fl(fl(x)\div fl(y)) = (fl(x) \div fl(y))(1+\epsilon_2)
$$
​	Onde $|\epsilon_i| < \eta$ .Logo os *erros relativos* permanecem pequenos.