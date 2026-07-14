## 🚀 React-Integracao-Omdb-Api-Node
Exemplo de integração com API OMDb em React 19 e Node.js com autenticação Jwt e banco de dados SQL-Server.

#### 📋 O que voçê vai ver nesse Projeto

| Tecnologia | Descrição |
|-----------|------------|
| **BCrypt** | Algoritmo de hashing criptográfico utilizado para armazenar senhas de forma segura |
| **LocalStorage** | Armazenamento em cache de dados no navegador de forma persistente em pares de chave e valor |
| **Jest** | Ferramenta framework de testes |
| **JWT** | É um crachá digital usado para identificar usuários e trocar informações de forma segura entre computadores |
| **Swagger** |	Conjunto de ferramentas para modelagem, documentação e teste de APIs RESTful |

#### 💬 Requisitos do Projeto
- Criar usuario no site API OMDb e copiar o **Chave Key** para poder fazer consultas da API [OMDb API](https://www.omdbapi.com/)
- Necessário configurar arquivo **.env**

Modifique alterando [DB_PASSWORD] , [SEU_KEY_OMDb] e [SEU_JWT_SECRET_KEY] no arquivo **.env** .
```bash
DB_HOST=127.0.0.1
DB_PORT=1435
DB_USER=sa
DB_PASSWORD=[SUA_SENHA]
APP_DATABASE=FilmesDB
OMDB_API_KEY=[SEU_KEY_OMDb]
JWT_SECRET=[SEU_JWT_SECRET_KEY]
```

#### 🔄 Executar a aplicação

## 📁 Backend
VSCode Terminal [1]
```bash
npm install 
cd backend
node src/scripts/create-database.cjs
npx tsx src/test-db.ts
```

- Para executar a aplicação 
```bash
npx tsx src/index.ts 
```

| HOST | URL |
|-----------|-----------|
| **Servidor** | http://localhost:3000/ |
| **Swagger** | http://localhost:3000/api-docs/ |
| **Ping/Pong** | http://localhost:3000/api/ping |
| **Conexão** | http://localhost:3000/api/test-db |
| **Health** | http://localhost:3000/api/health |

## 📁 Frontend 
VSCode Terminal [2]
```bash
npm run dev
```

O Projeto é Frontend é executado em **http://localhost:5173/**

#### 🔍 Executar Testes Unitários

VSCode Terminal [3]
```bash
npx jest
```

##### ⚙️ Configurar SQL-Server IP Estático  

O SQLSERVER funcionária na porta **TCP/IP 1435** para não gerar conflitos com a porta padrão **1433**

##### 

**Passo 1:** Abra o **SQLServer Configuration Manager** 
- No lado direito, Clique em Configuração de rede -> Protocolos para SQLEXPRESS e selecione a opção TCP/IP
- Em (Propriedades). Na aba Protocolo, mude a opção Enabled para Yes (caso esteja No).
- Agora, mude para a aba IP Addresses (Endereços IP). Role a janela até o final, lá embaixo na seção **IPAll**. Limpe completamente o campo **TCP Dynamic Ports** (deixe em branco, apague o 0 se tiver).
- No campo TCP Port, digite **1435**. Clique em Aplicar e depois em OK. 
- Por ultimo o principal Limpe completamente o campo **Portas TCP Dinamicas**

**Passo 2:** Reiniciar o serviço do Banco de Dados do SQL Server, somente vai ler essa nova porta se for reiniciado.

Confira sempre que necessário a porta no **SSMS (SQL Server Management Studio)**

```bash
SELECT 
    listener_id, 
    ip_address, 
    port 
FROM sys.dm_tcp_listener_states;
```


