# Berçário
  Sistema que manuseia dados de um berçário. Possui tabelas que instaciam objetos com características como: nome, aata de nascimento, altura, etc. Cada tabela é associada com a outra, a fim de proporcionar o bom funcionamento do sistema.

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
