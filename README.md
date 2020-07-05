# Guia de consulta rápida MongoDB
![Guia de consulta rapida](IMAGENS/banner.png)

## Introdução
Esse documento foi criado com o objetivo de facilitar a consulta de comandos do banco de dados MongoDB.

## Preparação de ambiente

### Pasta padrão dos bancos
Antes de iniciar, crie o caminho padrão aonde será salvo seus bancos de dadoss:
```
C:\data\db
```

## COMANDOS DE INICIALIZAÇÃO

### Iniciando o servidor

Para iniciar um servidor do MongoDB, execute o comando ```mongod``` através do CMD o seguinte comando e mantenha a janela aberta para manter ativo o servidor.
```Shell
 C:\Users\meuPC> mongod
```

### Abrindo uma conexão com o banco

Para abrir uma conexão com o servidor ativo, abra um novo terminal do windows e execute o comando ```mongo```
```Shell
 C:\Users\meuPC> mongo
```
## Tipos de dados

Alguns dos tipos de dados oferecidos pelo mongoDB diferentes:

| tipo de dado | Descrição                                                    | Exemplo                    |
|--------------|--------------------------------------------------------------|----------------------------|
| `double`     | Valor numérico de dupla precisão                             | 13.47                      |
| `integer`    | Armazena valores numéricos inteiros                          | 10                         |
| `string`     | Armazena valor em texto                                      | "felipe aguiar"            |
| `array`      | Armazena uma matriz de informações                           | ["tag1","tag2","tag3"]     |
| `boolean`    | Armazena valores de "verdadeiro" e "falso"                   | true                       |
| `objectId`   | Gera valores de códigos únicos, rápidos de gerar e ordenados |  objectId()                |
|              |                                                              |                            |





## DATABASE

Os databases são os containers que armazenam as coleções de documentos, são os bancos de dados propriamente dito.

#### Ativar ou criar (caso não exista) um database
```js
  use DATABASE_NOME
```

#### Mostra nome do banco atual
```js
  db.getName()

  //ou utilize apenas

  db
```

#### Listar todos databases dispoíveis
```js
  show dbs
```

#### Deletar database
```js
  db.dropDatabase()
```

#### Ver overview do banco
```js
  db.stats()
```

## COLEÇÕES
  Coleções são grupos de documentos BSON, são como se fossem 

#### Criar uma coleção préviamente
```js
  db.createCollection("nomeDaColeção")

  //saída: cria uma coleção com o nome passado.
```

#### Criar uma coleção automáticamente (caso não exista)
```js
  db.produtos.insert({"nome":"notebook"})

  /* outra maneira de criar uma coleção é inserir qualquer documento informando uma coleção, 
     aqui é inserido um documento na coleção produtos, caso ela não exista, será criado automáticamente. */
```

#### Listar coleções da base de dados ativa
```js
  show collections
```

#### Deletar uma coleção
```js
  //deleta coleção 
  db.NomeDaColecao.drop()

  //ou passando o nome da coleção via string
   db.getCollection("NomeDaDolecao").drop();
```


## DOCUMENTOS
  São os 'registros' de um banco feito em mongoDB, são basicamente objetos JSON salvos em formato binário (BSON).

#### Inserindo um documento
```js
// insere um documento na coleção pessoas

db.pessoas.insert(
    {
      "nome":"felipe aguiar",
      "habilidades":["Javascript","HTML","CSS3"],
      "criado_em": new Date()
    }
  )
```

#### Inserindo multiplos documentos
```js
  //passar um vetor de documentos JSON a serem inseridos na coleção de pessoas

  db.pessoas.insert(
    [
      {
        "nome":"felipe aguiar",
        "habilidades":["Javascript","HTML","CSS3"],
        "criado_em": new Date()
      },
      {
        "nome":"F. Aguiar",
        "habilidades":["NodeJS","Express","Knex"],
        "criado_em": new Date()
      }
    ]
  )
```

#### Consultando documentos
```js
  //seleciona tudo, equivalente ao select * from tabela
 db.pessoas.find() 
```

#### Consulta formatada para visualização em formato Json
```js
  //melhora visualização
  db.pessoas.find().pretty  
```

#### Consulta com filtro de pesquisa
```js
  db.pessoas.find({name:"mouse"})
```






