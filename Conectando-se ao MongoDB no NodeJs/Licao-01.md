# Usando bibliotecas de cliente MongoDB Node.js

## Instalação

A maneira recomendada de começar a usar o driver Node.js 5.x é usar o npm (Node Package Manager) para instalar a dependência em seu projeto.

Depois de criar seu próprio projeto usando npm init, você pode executar:

```shell
npm install mongodb
# or ...
yarn add mongodb
```
Isso fará o download do driver MongoDB e adicionará uma entrada de dependência em seu arquivo package.json.

Se você for um usuário Typescript, precisará das definições de tipo Node.js para usar as definições do driver:

```shell
npm install -D @types/node
```

## Extensões de driver

O driver MongoDB pode opcionalmente ser aprimorado pelos seguintes pacotes de recursos:

### Mantido pelo MongoDB:

- Compactação de rede Zstd - @mongodb-js/zstd
- Nível de campo MongoDB e criptografia consultável - mongodb-client-encryption
- Autenticação GSSAPI/SSPI/Kerberos - kerberos

Alguns desses pacotes incluem extensões C++ nativas. Consulte o guia de solução de problemas aqui se você tiver problemas de compilação.

### Terceiro:

- Compactação de rede Snappy - snappy
- Autenticação da AWS - @aws-sdk/credential-providers

## Exemplo rápido

Este guia mostrará como configurar um aplicativo simples usando Node.js e MongoDB. Seu escopo é apenas como configurar o driver e executar as operações CRUD simples. Para uma cobertura mais aprofundada, consulte a documentação oficial.
Crie o arquivo package.json

Primeiro, crie um diretório onde seu aplicativo ficará.

```shell
$ mkdir meuprojeto
$ cd meuprojeto
```

Digite o seguinte comando e responda às perguntas para criar a estrutura inicial do seu novo projeto:

```shell
$ npm init -y
```

Em seguida, instale o driver como uma dependência.

```shell
$ npm instalar mongodb
```