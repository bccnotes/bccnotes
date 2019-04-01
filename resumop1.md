# Resumo pré p1

***

## Bags Queues Stacks

- Bag é uma ADT iteravel que possui asoperação de : 
  - add
  - Em suma : é uma pilha da qual voce não remove elelementos
  - Serve pra simplesmente agrupar conteudo e iterar sobre eles
- Queue é uma ADT iteravel que segue a filosofia de FifO : FIst in, First out. Possui as operações : 
  - Enqueue: Empilha
  - dequeue : desempilha
- Stack :  ADT iterável  que segue a filosofia de LIFO : last in first out. Possui s operações
  - Push : empilha
  - pop : desempilha



------

### Genericos :

  Colocando a notação <ITEM> na definição de uma classe torna ela generica para instanciação de um objeto. Ao instanciar esse objeto, deve-se especificar o tipo dele, na forma : 

```java
  Stack<String> s = new Stack<String>();
```





### Iteradores

- Uma classe implementa a interface iteravel se : 

  - Implementa um metodo "Iterator", que retorna um objeto iteravel

    - ```java
      public Iterator<Item> iterator() {
          return new OBJETOITERAVEL();
      }
      ```

    - 

    - OBS.: Um objeto iteravel é um objeto que possui as operaçẽos next(), hasNext(), remove().

  - Importa a interface do iterator : import java.util.Iterator

  - Se compromete a implementar um método iterador, especificando , ao lado do nome da classe, a seguinte instrução : 

    ```java
    implements Iterable<Item>
    ```

  - OBS : Arrays NÃO são iteraveis. O Java aceita usar forEach com um array, mas ele não é um objeto iteravel.



------

## Union Find

- Coleção disjunta dinâmica : É uma coleção de vertices modificados ao longo do tempo para os quais a intersecção de qualquer par grupo de vertices vale 0.

- O union find tem duas operações elementares : 

  - find : busca o representante daquela coleção
  - Union : junta duas coleções

- Ideia de estrutura para um Union Find. Dado um conjunto de itens, crio um array tal que id[i] denota qual coleção o i pertence.



  - O elemento tal que id[i] = i id da coleção de i
  - Esse tipo de algoritmo se chama **quick-find**, no qual é muito facil descobrir qual a coleção na qual o meu elemento pertence (é só fazer um acesso em arr[i])
  - Em contrapartida, o union é o(N), porque para unir dois caras, eu tenho que percorrer o arr e mudar o id de um dos grupos para o id do outro grupos

- **Quick-Union** : Faz uso da ideia de **Florestas disjuntas**, mudando a ideia do array tendo que id[ i ] = pai de i. Vamos renomear o array para pai[ ].

  - Se id[ p ] == p, então p é o representante da coleção.

  - Para unir duas florestas disjuntas, nos juntamos a raiz de uma com o outro elemento

  - Agora o union fica muito rapido : fazendo union(p, q) basta fazer pai[find(p)] = pai[find(q)].

  - Mas o find fica um pouco pior... para achar o representante de uma coleção, eu tenho que ficar fazendo find(P) até eu achar um cara tal que find(p) == p.

- **Weighted quick union** : O quick union tem um problema : se eu fizer union(p, q) e se p <<<< q, p vira o pai de q. Agora imagine que estou fazendo varias operações de union(p, q) e q sempre é um unico nó, voce cria uma coleção linear. Dai o find(p) sempre será O(N), sendo que dava pra fazer algo como O(log n) se eu inserisse de forma esperta.

  - O **weighted quick union** resolve isso sempre fazendo a coleção de maior tamanho ser a coleção pai. Isso é feito usando um array de tamanho da coleção ( sz [ ]). O tamanho de uma coleção é dado por sz [ i ], para todo i de uma mesma coleção ele retorna o mesmo valor.
    - Isso garante que o o find (e o union, porque ele depende do find) sejam O( log n ).
  - obs : Isso garante tambem que toda arvore com altura h tem pelo meons 2^h nós.

- **Path Compression** :  É muito interessante encurtar os caminhos durante cada find. Se o find sempre quer procurar o representante de uma coleção, por que não conectar todos os filhos ao representante?

  - Isso é feito dentro do find : 

    ```java
    public in find(int p) {
        if (p != pai[p])
            pai[p] = find(pai[p]); // chamo a recursão pro pai, e na volta da recursão vai atribuindo todos elementos ao representante geral
        return pai[p];
    }
    ```

    * Isso torna o find e o union amortizado O(lg * n) - mas na prática amortizado é O(1).

***



### Heaps

* Estrutura de dados que mantém as seguinte regras : 

  * Um elemento pode ter dois filhos
    * O filho esquerdo de um elemento i vale 2*i
    * O filho direito de um elemento i vale 2*i + 1
    * O máximo elemento a ter filho esquerdo vale n/2
    * O heap começa a ser indexado a partir de 1
  * Um max heap é um heap que segue a regra : 
    * Para todo nó i, i é maior que seus filhos

* Dado um vetor, como transforma-lo em um heap? Usando a operação básica do **sink**

  * O sink parte do principio que recebe um heap **quase perfeito** : Um elemento i está fora do lugar, e os filhos de i já são heaps. O sink "afunda" i no lugar certo do heap.

  ``` java
      private void sink(int i) {
          // faz o sink do índice i do heap.
          // um elemento i tem filho esquerdo se i <= n/2
          // um elemento i tem filho direito se i <= n/2+1
          // assumo aqui que só vou chamar o sink se o elemento i tiver um filho.
          if (i <= this.n/2) {
  
              int lrg = maior(i); //acha o maior dos filhos de i
              if (lrg == i)
                  return;
  
              if (lrg == esq(i)) {
                  swap(esq(i), i);
                  sink(esq(i));
              }
  
              else {
                  swap(dir(i), i);
                  sink(dir(i));
              }
          }
  
      }
  ```

  Partindo so sink, podemos transformar um vetor num heap. Basta fazer : 

  ```java
  private void heapfy() {
       for(int i = this.n/2; i>=1; i--) {
           sink(i);
       }
  }
  ```

  Existe uma operação similar ao sink chamado **swim** que é utilizado pra adcionar um elemento numa fila de prioridade : 

  ```java
      private void swim(int i) {
  
          for (int j = i; j > 1; j = j/2) {
              if (this.heap[j] < this.heap[j/2])
                  break;
              else {
                  swap(j, j/2);
              }
          }
      }
  ```



  * Fila de prioridade : É um heap para o qual os itens de maior valor ficam no topo (é um max heap)
    * Operações basicas : 
      * add : Adciona o item na fila de prioridade. Voce coloca o elemento no fim do array e faz **swim** nele
      * Remove: Troca o primeiro elemento com o ultimo, tira o ultimo da lista, e faz **sink** do primeiro.

 



## Leftist Heap

***

### Leftist Tree

* Cada nó de uma árvore esquerdista tem a seguinte estrutura  : 

  ```java
  +-----+-----+
  |item |dist |
  |     |     | 
  +-----+-----+
  |left |right|
  |     |     |
  +-----+-----+
      
  private class Node {
  	private Item item;
  	private Node left, right;
  	private int dist;
  }
  ```

* Dist : é o **número de passos entre nós até você cair num campo nulo**, ou seja : 

  * r.dist = 0, se r == null

  * r.dist = 1 + min(r.left.dist, r.right.dist), se r!=null

  * Em outras palavras, a **o dist de um nó é 1 a mais que o nó filho com menor dist**

    ***

    **Uma árvore é dita esquerdista se **
    $$
    r.right.dist \leq r.left.dist
    $$

    ***

    Ou seja : é *mais fácil* achar um campo nulo seguindo sempre pela direita do que pela esquerda.

    Por isso, podemos dizer que **r.dist = r.right.dist+1** numa arvore esquerdista.

  * Se r é um nó de uma arvore esquerdista com n nós da subarvore que o tem como raiz, então : 
    $$
    n \geq 2^{r.dist}-1 \rightarrow n\geq 2^{r.right.dist+1}-1
    $$
    Podemos manipular a expressão e obter : 
    $$
    n' \geq 2^{r.right.dist}\times2 - 1 \\ \therefore \\ n'\geq \frac{2^{r.dist}}{2} - 1
    $$
    Avaliando para o filho esquerdo : 
    $$
    n* \geq 2^{r.left.dist}-1 \therefore n* \geq 2^{r.dist}* k - 1
    $$








Sendo $k \geq 1$, pois a arvore esquerdista possui distancia esquerda maior ou igual que a atual. Dessa forma concluimos que : 
$$
n* \geq n
$$
Mas
$$
n \geq n' \implies n* \geq n'
$$
Assim nós concluímos que **existem menos (ou o mesmo número de) elementos à direita do que a esquerda de um nó**.

Como sabemos que a altura de um nó numa arvore é dada por log(n/r), a altura da subarvore a direita de um dado nó é com certeza menor ou igual a subarvore da esquerda.

  * Eu fiz tudo isso pra poder argumentar que, ao fazer um merge de dois leftist heaps, **é mais vantajoso olhar para a subarvore direita do leftist heap**.

    ### Merge

    ```java
    private void merge(node r1, node r2) {
        if (r1 == null) return r2;
        if (r2 == null) return r1;
        
        if (r1.item < r2.item)
            	swap(r1,r2);
        r1.right = merge(r1.right, r2);
    }
    ```


  * O código acima mistura os dois heaps, mas não preserva a propriedade de esquerdismo. A seguir um código que faz isso : 

  ```java
  private Node merge(Node r1, Node r2) {
  	if (r1 == null) return r2;
  	if (r2 == null) return r1;
  // r1 != null e r2 != null
  	if (less(r1, r2)) {
  	Node tmp = r1; r1 = r2; r2 = tmp;
  }
  // r1 aponta para o maior item
  	if (r1.left == null) r1.left = r2;
  	else {
  		r1.right = merge(r1.right, r2);
  		if (r1.left.dist < r1.right.dist) {
  		// exchange left and right
  			Node t = r1.left;
  			r1.left = r1.right;
  			r1.right = t;
  		}
  		r1.dist = r1.right.dist + 1;
  	}
  return r1;
  }
  ```



  Explicando o que acontece : 

  * Eu mantenho o item de maior prioridade no r1
  * Vou chamando a função para o r1.right (percorro pela direita porque é o menor caminho, como especificado acima)
    * Se eu chegar em algum momento que o r1 tem um filho esquerdo nulo, jogo todo o r2 pra esquerda de r1
  * Se alguma operação quebrar a propriedade de leftist, eu simplesmente troco os filhos
  * Repito até chegar em um filho nulo

***

## Tabela de símbolos



* São estruturas chave,valor

* cada chave é única

* Nenhum valor é nulo 

* Operações basicas

  * put : insere (se a chave inserida for nula, trato como deleção)
  * get (key): devolve a chave. Se não achar, reotrna nulo
  * delete (key) : deleta a chave.
  * isEMpty : verifica se a tabela está vazia
  * contains (key) : verifica se a chave esta na tabela
  * keys() : retorna um iteravel com todas as chaves

  ***

  ### Implementação em vetor ordenado

  * Podemos construir uma tabela de símbolos num vetor ordenado, com o qual temos a vantagem de **indexar** as chaves. Isso pode nos ajudar a implementar uma **busca binária**.

  * Nesse caso teriamos tambem um vetor de **valores**, que armazena cada valor em um indice do array.

  * O vetor de **Keys** armazena as chaves para cada valor. As chaves podem ser strings, numeros, qualquer coisa. **Os índices do vetor apenas fazem a "conexão" entre a chave e o valor. O indice de um par chave, valor deve ser igual nos dois vetores** 

  * ex : 

    * Keys : ["carro", "bolacha", "caderno"]

    * Valor : ["Um veículo de implosão interna", "Alimento de trigo assado", "Aparato para anotar coisas"]

    * Fazendo rank("carro"), retorna o número 0. Então se fizermos get("carro"), a função retorna values[0] que é "Um veículo de implosão interna"

    * A operação básica dessa estrutura é o **rank** que retorna o indice no array de uma key. É basicamente uma busca binaria : 

    * ```java
      
      private Key[] keys;
      private Value[] vals;
      private int n = 0;
      public BinarySearchST(cap) { // constutor, cria uma ST de tamanho cap
      	keys = (Key[]) new Comparable[cap]; // as chaves são comparaveis. Precisa implementar um metodo compareTo
      	vals= (Value[]) new Object[cap];
      }
      public int rank(Key key) {
          int lo = 0; int hi = n - 1;
          while (lo <= hi) {
              int mid = (lo+hi)/2;
              int cmp = key.compareTo(keys[mid]);
              if(cmp == 0)
                  	return mid;
              if(cmp < 0) // key < keys[mid]
                  	hi = mid - 1; 
             	if(cmp > 0)
                  	lo = mid + 1;
          }
          
          return lo; // por que ?
      }
      
      public Value get( Key key ) {
          int i = rank(key);
          if(i < n && key.equals(keys[i]))
              	return vals[i];
          return null;       
      }
      
      public void put(Key key, Value val) {
          int i = rank(key);
          if (i < n && key.compareTo(keys[i]))
              	vals[i] = val; // tenho um vetor de valores
          if (n == keys.length)
              	resize(2*keys.length);
          for(int j = n; j > 1; j--) {
              keys[j] = keys[j-1];
              vals[j] = vals[j-1];
          }
          keys[i] = key; vals[i] = vals; // i == 0 nesse caso
          n++;
      }
      
      public void remove(Key key) {
      	if (isEmpty()) return;
      	
          int i = rank(key);
      	if (i == n || !key.equals(keys[i])) // se o item não estiver na ST
      		return;
          
      	for (int j = i; j < n-1; j++) { // faz o shift de todo mundo para tras, sobrescrevendo o item a ser removido
      		keys[j] = keys[j+1];
      		vals[j] = vals[j+1];	
      	}
          
      	n--;
      	keys[n] = null; vals[n] = null; // remove o valor duplicado de keys[n]
      	if(n > 0 && n == keys.length/4)
      		resize(keys.length/2); // downsize
      	}
      }
      
      
      ```

  ### Análise de tempo

  * A criação de uma tabela de símbolos é $O(n^2)$ por causa dos shifts de varios puts. Fazendo varias inserções no começo, teriamos : 

  * $$
    1 + 2 + 3 + ... n-1 = \sum_{i=1}^{n-1}i  = \frac{n^2}{2} = O(n^2)
    $$

    Consumo do get : lg(n);

  * Consumo do put : O(n)

  * Consumo do remove : O(n)

  ### Problemas dessa implementação 

  * Alto consumo de espaço
  * Criação de tabela pode ser bem demorada no pior caso

  ***

  ### Implementação com lista ligada

  * Cada nó tem os campos : 

    * Key : chave
    * val ; valor associado à chave
    * next : proximo node

  * Consturotr : cria uma variavel n com a quantidade de itens e seta o primeiro item da lista.

  * Implementação : 

    ```java
    public Node rank(Key key) {
        // acha o nó anterior ao com chave igual a key
        Node p = first;
        Node q = first.next;
        while (q != null && p.key.compareTo(key) != 0) {
            p = q;
            q = q.next;
        }
        return p; // aponta para o ultimo da lista nesse caso
        //roda em o(n)
    }
    
    public Value get(Key key) {
        // retorna o valor associado á chave key
        Node p = rank(key);
        Node q = p.next;
        
        if (q != null)
            return q.val;
        return null;
        //o (n) devido ao rank
    }
    
    public void put(Key key, Value val) {
        Node p = rank(key);
        Node q = p.next;
        if( q != null)
            q.val = val;
        else{
            Node t = new Node(key, val, first);
            first = t;
        }
        n++;
        //consoe o(N) devido ao rank
    }
    
    public void delete(Key key) {
        //deleta da lista o valor com chave key
        Node p = rank(key);
        Node q = p.next;
        if(q != null) {
            p.next = q.next;
            q.next = null;
        }
        
        n--;
        // consome o(n) devido ao rank.
    }
    ```

  * O consumo de tempo de criar essa tabsim é o mesmo da tabela de array duplo

  * Essa implementação ocupa menos espaço (acho) mas o get é mais lento

    ### Custo de busca

    Digamos que cada chave i tem uma probabilidade de ser acessada igual a pr[i]. Então, uma busca bem sucedida pode ser calculada pela esperança : 
    $$
    T(n) = Pr[0] + 2Pr[1] + \dots nPr[n-1]
    $$

* Isso é o calculo da esperança do custo médio das operações de consulta. A consulta de um nó K exige K+1 comparações. Portanto, multiplicamos o valor do número de comparações pela probabilidade de cada termo ser acessado

* * Esse custo médio **diminui** se as chaves são ordenadas com ordem decrescente de probabilidade, isto é, **se colocarmos as chaves mais acessadas primeiro**.

* ***





### Self-organizing lists

* É um tipo de busca que re-organiza a table conforme as buscas são feitas.
* **Método move to front (MTF)** : Sempre que uma chave é acessada, joga pro começo
  * Problema : pode super valorizar chaves pouco acessadas.
    * No entanto, isso é rapidamente resolvido recolocando na frente o item mais acessado.
  * Positivo : Facil de implementar, não uitliza espaço extra e se adapta rapidamente À sequência de acessos
* **Método do contador** : Mantém um contador de acessos nos nodes
  * Problema : precisa de espaço extra
  * Positivo : reflete muito bem o padrão de acesso
* **Método da Transposição** : Sempre que consultar uma chave, troca com seu predecessor (Caso ele exista)
  * Positivo : evita super valorização de chaves pouco acessadas; Itens no começo provavelmente são os mais acessados.  E caso não seja, o item ja estava no começo antes então de boa
  * Desvantagem : Demora pra colocar o mais acessado no começo (se for uma tabela muito grande, acaba não fazendo efeito, só se o item for MUITO acessado)

### Tempo

![](/home/caio/Imagens/tempo.png)

Pelas diferenças de tempo dentro da mesma estrutura, da pra ver como a ideia mtf é poderosa. Mas o log(n) do vetor ordenado ainda supera todos.

***

## Skip Lists

* A ideia de uma skip list é ter um vetorzão mantendo todos os niveis de uma skip. 

***



## Árvores Binárias

* É um conjunto de nós. Cada nó tem tres campos : 

  * item (generico) : conteudo
  * left(Node) : filho esquerdo
  * rigth(Node) : filho direito

* Um nó r é descendente de p se r pode ser acessado com operações sucessivas de p = p.left e p = p.right

* Toda árvore binaria tem um **endereço**, que é um ponteiro node para sua raiz. r é uma arvore binaria se : 

  * r é nulo
  * r.left e r.right são arvores binarias

* **Percursos** : existem tres percursos pra percorrer uma AB

  * inOrder(ERD) : Esquerda Raiz Direita
  * PreOrdem(RED) : Raiz Esquerda Direita
  * PosOrdem(EDR) : Esquerda Direita Raíz
  * Tal artifício é util pra gerar um iteravel para a AB (voce pode empilhar os itens em uma dada ordem e retornar a pilha, que é iterável!).

  ```java
  public void inOrdem(Node root, Queue<Item> q) {
      if(root != null) {
          inOrdem(root.esq,q);
          q.enqueue(root.item);
          inOrdem(root.dir,q);
          return q;
      }   
  }
  
  public void preOrdem(Node root, Queue<Item> q) {
      if(root != null) {
          q.enqueue(root.item);
          preOrdem(root.esq, q)
          preOrdem(root.dir, q);
          return q;
      }
  }
  
  public void posOrdem(Node root, Queue<ITem> q) {
      if(root != null) {
          posOrdem(root.esq, q);
          posOrdem(root.dir, q);
          q.enqueue(root.item);
          return q;
      }
  }
  ```



  * **Profundidade** : A profundidade de um nó é o numero de links no caminho da raiz até o nó.
  * **altura** : É o maximo da profundidado dos nós.
    * **A altura de uma árvore e um numero entre lg n e n**

  ### Árvores balanceadas

  * Uma árvore é balanceada se, em cada um de seus nós, **as subárvores direitas e esquerdas tem aproximadamente a mesma altura**. 
  * Podemos ter arvores com um campo extra no nó : o endereço do nó pai.

  ``` java
  // codigo que acha o sucessor de um dado no r
  // aqui usamos uma arvore BALANCEADA na qual temos acesso ao nó // pai
  
  public Node sucessor(Node r) {
      if(r.right != null) {
          node q = q.right;
          while(q.left != null) 
             	q = q.left;
          return q;
      }
      
      while(p.prnt != null && p.prnt.right == p) // o ultimo and garante que estou andando pelo caminho da direita. Quando ele deixar de ser verdadeiro significa que terminei o caminho da direita e estou na raiz
          p = p.prnt;
      return p;
      
  }
  ```
