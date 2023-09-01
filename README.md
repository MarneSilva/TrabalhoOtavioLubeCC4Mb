# Berçário
  Sistema que manuseia dados de um berçário. Possui tabelas que instanciam objetos com características como: nome, data de nascimento, altura, etc. Cada tabela é associada com a outra, a fim de proporcionar o bom funcionamento do sistema.

# Passos para iniciar o projeto Node e Typescript

 ## Iniciando o node
 npm init -y
 ## Instalar o typescript
 npm install typescript --save-dev
 ## Inicializar e Configurar o Typescript
 npx tsc --init
## Configurar o config.ts
 Modelo recomendado para as configurações:
 
 {
   "compilerOptions": {
    "target": "es2016",
    "module": "commonjs",
    "rootDir": "./src",
    "outDir": "./dist",
    "esModuleInterop": true,
    "forceConsistentCasingInFileNames": true,
    "strict": true,
    "skipLibCheck": true
  }
}

# Passos para iniciar o projeto Prisma e o Prisma Client

  ## Instalar o typescript node
  npm install typescript ts-node @types/node --save-dev
  ## Instalar o Prisma CLI
  npm install prisma --save-dev
  ## Inicializar o Prisma
  npx prisma init --datasource-provider sqlite
  ## Incrementar um modelo genérico de banco de dados no prisma.scheme
  O modelo sugerido pelo site do Prisma é esse:
  
  model User {
  id    Int     @id @default(autoincrement())
  email String  @unique
  name  String?
  posts Post[]
}

model Post {
  id        Int     @id @default(autoincrement())
  title     String
  content   String?
  published Boolean @default(false)
  author    User    @relation(fields: [authorId], references: [id])
  authorId  Int
}

**IMPORTANTE:** Não retire nada do código original já encontrado do arquivo, apenas adicione este código apresentado na última linha vazia disponível.

## Gere um Prisma Client baseado no modelo incrementado no prisma.scheme
npx prisma generate
## Implemente a importação do Prisma Client no arquivo que você deseja utilizá-lo e teste
Crie um arquivo typescript no seu projeto, seja ele dentro de uma outra pasta chamada src, com o nome de teste.ts ou qualquer outro nome. Após ter feito isso,
adicione este código ao início do arquivo:

import { PrismaClient } from '@prisma/client/edge'
const prisma = new PrismaClient()

Caso o seu editor de texto apresente algum erro na linha de código da importação do Prisma Client, significa que você pulou alguma parte das etapas, e o Prisma não foi instalado corretamente. Revise as etapas a procura de alguma que tenha passado despercebido, e caso não encontre, tente também pesquisar o seu erro na internet ou recomeçar um novo projeto.

# Como utilizar queries e conectar o banco de dados

## Use o Prisma Migrate para criar o banco de dados
npx prisma migrate dev --name init

**IMPORTANTE:** A pasta prisma.rar já possui uma migração feita em seu histórico, mas realize o comando novamente, com o modelo lógico desejado no esquema do prisma.

## Escreva queries de criação de tabelas e inserção de dados no arquivo Typescript desejado
Siga esta estrutura:

import { PrismaClient } from '@prisma/client'
import { create } from 'domain'
const prisma = new PrismaClient()

async function main() {
    const Example = await prisma.example.create({
      data: { // Campos da table }
    })
    // Insira aqui todas as queries parecidas com esta acima
}
// Mandar as queries para o banco de dados
main()
    // O que fazer depois da promessa retornar (as queries serem enviadas)
    .then(async () => {
    await prisma.$disconnect()
    })
    // Catch para demonstrar o erro no console
    .catch(async (e) => {
    console.error(e)
    await prisma.$disconnect()
    process.exit(1)
})

## Rode com a aplicação do ts-node no terminal
Entre no diretório em que se encontra o seu arquivo Typescript. No caso do projeto, é o diretório src dentro da pasta Typescript.
cd .\src\
Depois disso, rode no terminal o código:
npx ts-node bercario.ts
Substitua bercario.ts pelo nome do seu arquivo Typescript com as queries. Para este projeto, o nome do arquivo se chama bercario.ts.
Para visualizar os resultados, adicione o um console.log de uma constante no final da função assíncrona do seu arquivo Typescript.

