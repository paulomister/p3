# Manual de Instalação: Aplicação Corretor de Scripts

## Pré-requisitos

Antes de começar, certifique-se de ter as seguintes ferramentas instaladas no seu sistema:

1. **Node.js** (inclui o npm):
   - Baixe e instale a versão LTS (Long Term Support) do [Node.js](https://nodejs.org/).
   - Verifique a instalação:
     ```bash
     node -v
     npm -v
     ```

2. **Editor de Código** (recomendado: VS Code):
   - Baixe e instale o [Visual Studio Code](https://code.visualstudio.com/).

---

## Passo 1: Configurar o Back-end (NestJS)

1. **Navegue até a pasta do back-end:**
   - Se você já tem a estrutura do projeto, navegue até a pasta `back-end`:
     ```bash
     cd back-end
     ```

2. **Instale as dependências do back-end:**
   - Execute o comando para instalar todas as dependências:
     ```bash
     npm install
     ```

3. **Execute o back-end:**
   - Para rodar em modo de desenvolvimento:
     ```bash
     npm run start:dev
     ```
   - O servidor estará disponível em `http://localhost:3000`.

---

## Passo 2: Configurar o Front-end (React)

1. **Navegue até a pasta do front-end:**
   - Se você já tem a estrutura do projeto, navegue até a pasta `front-end`:
     ```bash
     cd front-end
     ```

2. **Instale as dependências do front-end:**
   - Execute o comando para instalar todas as dependências:
     ```bash
     npm install
     ```

3. **Configure o proxy para o back-end:**
   - No arquivo `package.json` do front-end, adicione a linha abaixo para evitar problemas de CORS:
     ```json
     "proxy": "http://localhost:3000"
     ```

4. **Execute o front-end:**
   - Inicie o servidor de desenvolvimento:
     ```bash
     npm start
     ```
   - O front-end estará disponível em `http://localhost:3000`.

---

## Passo 3: Integrar Back-end e Front-end

1. **Faça requisições do front-end para o back-end:**
   - No arquivo `src/App.tsx` do front-end, adicione um exemplo de requisição usando `axios`:
     ```typescript
     import React, { useEffect, useState } from 'react';
     import axios from 'axios';

     function App() {
       const [message, setMessage] = useState('');

       useEffect(() => {
         axios.get('/')
           .then((response) => setMessage(response.data))
           .catch((error) => console.error(error));
       }, []);

       return (
         <div>
           <h1>Corretor de Scripts</h1>
           <p>Resposta do back-end: {message}</p>
         </div>
       );
     }

     export default App;
     ```

2. **Teste a integração:**
   - Certifique-se de que o back-end está rodando (`npm run start:dev` na pasta `back-end`).
   - Execute o front-end (`npm start` na pasta `front-end`).
   - Acesse `http://localhost:3001` e veja a resposta do back-end.

---

## Passo 4: Executar a Aplicação Completa

1. **Back-end:**
   - Na pasta `back-end`, execute:
     ```bash
     npm run start:dev
     ```

2. **Front-end:**
   - Na pasta `front-end`, execute:
     ```bash
     npm start
     ```

3. **Acesse a aplicação:**
   - Abra o navegador e acesse `http://localhost:3001`.

---

## Dicas Finais

1. **Versionamento com Git (opcional):**
   - Se você quiser versionar o projeto, inicialize um repositório Git na pasta raiz:
     ```bash
     git init
     ```
   - Adicione um `.gitignore` para evitar o versionamento de pastas como `node_modules`.

2. **Extensões do VS Code (opcional):**
   - Instale extensões como **ESLint** e **Prettier** para melhorar a produtividade.

3. **Deploy (opcional):**
   - Para deploy, você pode usar serviços como **Vercel** (front-end) ou **Render** (back-end).

---

## Resumo dos Comandos

### Back-end:
- Instalar dependências:
  ```bash
  npm install
  ```
- Rodar em desenvolvimento:
  ```bash
  npm run start:dev
  ```

### Front-end:
- Instalar dependências:
  ```bash
  npm install
  ```
- Rodar o servidor de desenvolvimento:
  ```bash
  npm start
  ```
