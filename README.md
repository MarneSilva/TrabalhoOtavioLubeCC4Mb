# Berçário
  Sistema que manuseia dados de um berçário. Possui tabelas que instaciam objetos com características como: Nome, Data de nascimento, Altura, etc. Cada tabela é associada com a outra, a fim de proporcionar o bom funcionamento do sistema.

# Passos para iniciar o projeto Node e Typescript

 ## Iniciando o node
 npm init -y
 ## Instalar o typescript
 npm install typescript --save-dev
 ## Inicializar e Configurar o Typescript
 npx tsc --init
## Configurar o config.ts
 Modelo recomendado para as configurações:
 
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

