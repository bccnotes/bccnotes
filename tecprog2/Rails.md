# Ruby on Rails

## O padrão MVC

### Model 

Consiste nos dados de uma aplicação, envolvendo a modelagem e as regras de maniplação destes. A convenção de arquivos model é: `nomeDaTabelaNoSinglar.rb`

### View

Parte referente a o que é mostrado ao usuário, envolve a representação dos dados. A convenção de arquivos view é: `nome.html.erb` (ou `haml` )

### Control

Faz a mediação entre o usuário e os dados armazenados. A conveção de arquivos controller é: `nome_controller.rb`

As ideias centrais por trás do MVC são a reusabilidade de código e a separação de conceitos. Cada "parte" do MVC está localizada em uma pasta dentro de `app`

## Sistema de pastas

**app/ -** Contém os controllers, models e views da aplicação.
**config/ - ** Configurações de regras, rotas, banco de dados, etc.
**db/ -**  Contém os schemas e migrations do banco de dados.
**doc/ - ** Documentação da aplicação.
**lib/ - **Bibliotecas de terceiros da aplicação.
**log/ -** Arquivos de log.
**public/ -** Imagens, JavaScript, CSS e outros arquivos estáticos.
**test/ -** Unit test.

## Modelando dados

Para criar uma tabela que representará um modelos de nossos dado, fazemos:

```ruby
ruby generate scaffold <Nome> <atributo>:<tipo>
```

Ou, em um exemplo concreto, se quisermos criar uma tabela que representará um contato, podemos fazer: 

```shell
ruby generate Scaffold Contato nome:string telefone:integer
```

As tabelas serão geradas na pasta `models`, enquanto suas `migrates` serão geradas em /db/migrate/.

## Migrations

## ActiveRecord

O ActiveRecord é um framework embutido no Rails que é responsável por fazer a tradução de Ruby para SQL para que seja possível fazer as requisições no bando de dados.