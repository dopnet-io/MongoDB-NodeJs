# Conectando-se a um cluster Atlas em aplicativos Node.js

## Criar um Cluster MongoDB

1. Crie um cluster de nível gratuito no Atlas

Crie um cluster MongoDB de nível gratuito no MongoDB Atlas para armazenar e gerenciar seus dados. MongoDB Atlas hospeda e gerencia seu banco de dados MongoDB na nuvem. Conclua o guia Introdução ao Atlas para configurar uma nova conta do Atlas, um cluster de nível gratuito (uma instância MongoDB compartilhada) e carregar dados de amostra em seu cluster.

2. Conecte-se ao seu cluster

Você pode se conectar ao seu cluster MongoDB fornecendo uma string de conexão que instrui o driver sobre onde e como se conectar. A string de conexão inclui informações sobre o nome do host ou endereço IP e a porta do cluster, o mecanismo de autenticação, as credenciais do usuário quando aplicável e outras opções de conexão.

Para se conectar a uma instância ou cluster não hospedado no Atlas, consulte Outras maneiras de se conectar ao MongoDB.

Para recuperar sua string de conexão para o cluster que você criou na etapa anterior, faça login em sua conta do Atlas, navegue até a seção Banco de dados e clique no botão Conectar para o cluster ao qual deseja se conectar, conforme mostrado abaixo.

![](https://www.mongodb.com/docs/drivers/node/current/includes/figures/atlas_connection_select_cluster.png)

Prossiga para a seção Conecte seu aplicativo e selecione o driver Node.js. Selecione a guia Connection String Only e clique no botão Copy para copiar a string de conexão para a área de transferência, conforme mostrado abaixo.

![](https://www.mongodb.com/docs/drivers/node/current/includes/figures/atlas_connection_copy_string_node.png)

## Conecte-se ao seu aplicativo

1. Crie seu aplicativo Node.js

Crie um arquivo para conter seu aplicativo chamado index.js no diretório do projeto. Adicione o código a seguir, atribuindo à variável uri o valor de sua string de conexão.

```js
const { MongoClient } = require("mongodb");

// Replace the uri string with your connection string.
const uri =
  "mongodb+srv://<user>:<password>@<cluster-url>?retryWrites=true&w=majority";

const client = new MongoClient(uri);

async function run() {
  try {
    const database = client.db('sample_mflix');
    const movies = database.collection('movies');

    // Query for a movie that has the title 'Back to the Future'
    const query = { title: 'Back to the Future' };
    const movie = await movies.findOne(query);

    console.log(movie);
  } finally {
    // Ensures that the client will close when you finish/error
    await client.close();
  }
}
run().catch(console.dir);
```

2. Execute seu aplicativo Node.js

Execute o aplicativo que você criou na etapa anterior na linha de comando:

```shell
$ node index.js
```
Você deve ver os detalhes do documento do filme recuperado na saída:

```json
{
  _id: ...,
  plot: 'A young man is accidentally sent 30 years into the past...',
  genres: [ 'Adventure', 'Comedy', 'Sci-Fi' ],
  ...
  title: 'Back to the Future',
  ...
}
```

Se você encontrar um erro ou nenhuma saída, verifique se você especificou a cadeia de conexão adequada no código do aplicativo e carregou o conjunto de dados de amostra em seu cluster Atlas.

Neste ponto, você deve ter um aplicativo funcionando que usa o driver Node.js para se conectar à sua instância do MongoDB, executa uma consulta nos dados de amostra e imprime o resultado.