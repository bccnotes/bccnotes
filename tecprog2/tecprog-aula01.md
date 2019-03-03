# Aula 01

### Referências Úteis : 

* https://www.quora.com/What-is-the-difference-between-HTTP-protocol-and-TCP-protocol - Diferença entre TCP e HTTP.

* https://www.techopedia.com/definition/24717/network-port - O que é uma porta?
* instalando o ruby : sudo apt-get install ruby-full

***

## Servidor Web

* O servidor fica online servindo arquivos e fica escutando uma **porta**.
  * A porta é o **identificador do processo sendo executado na rede**.
  * A rede manda pacotes para o servidor, por meio de protocolos de transporte (o utilizado pela internet é o **TCP/IP**). O TCP/IP é um protocolo de internet de dupla comunicação : o emissor conversa com o receptor antes de enviar o pacote em si, dessa forma ocorre uma verificação de segurança, então voce tem a garantia de que o pacote vai chegar inteiro. Outro protocolo é o **UDP**, que é de comunicação direta. Ele é mais rápido, mas menos seguro (serviços de streaming usam UDP normalmente).
  * A rede também usa protocolos de aplicação, como o HTTP.

***

## Serviço web

* Um serviço web possui, por definição, um banco de dados.

***



## Padrão REST

* Padrão de comunicação entre servidor e Página, alguns comandos : **Get, Post, Put, Patch, Delete**.

***

## Ruby

* A linguagem ruby segue a filosofia de que **Convenção prevalece sobre configuração**
  * Exemplo, variaveis que começam com letra maiúscula são constantes
* Variáveis não possuem tipo, só os conteúdos das variáveis