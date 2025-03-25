# 📚 Library API

A Library API é uma API RESTful robusta, construída com Spring Boot, que oferece funcionalidades completas para gerenciamento de uma biblioteca digital. A aplicação inclui autenticação segura utilizando OAuth2,
 permitindo acesso controlado a recursos protegidos. A API oferece operações CRUD (Criar, Ler, Atualizar e Deletar) completas para gerenciar informações de autores e livros, com recursos avançados de busca 
dinâmica, que possibilitam consultas detalhadas com base em diferentes parâmetros.

Seguindo as melhores práticas da arquitetura REST, a API garante respostas HTTP adequadas para cada tipo de operação, incluindo o uso correto dos códigos de status e o envio de mensagens de erro precisas 
e informativas. Todos os erros são tratados de forma apropriada, com explicações claras no corpo da resposta, permitindo fácil compreensão e diagnóstico dos problemas.

## 🚀 Tecnologias Utilizadas

- **Spring Boot 3.3.4**
- **Spring Security + OAuth2** (Login social com Google)
- **Spring Data JPA**
- **MapStruct** para mapeamento de DTOs
- **Lombok** para reduzir boilerplate code
- **Spring Observer** para monitoramento
- **SpringDoc + Swagger** para documentação interativa
- **Thymeleaf** para páginas simples de autenticação
- **PostgreSQL** como banco de dados


## Funcionalidades🛸

### 1. **Autenticação e Autorização** 🔒

- **OAuth2 Authentication**: A API utiliza OAuth2 para autenticação segura dos usuários. 🔐
- **Login Social**: Suporte ao login social com Google e outros provedores de autenticação. 🌐
- **Geração de Token**: Geração de token de acesso com validade de 1 hora e suporte a refresh tokens para renovação. 🔄

### 2. **Operações CRUD para Autores** 📚✍️

- **Criar Autor**: Cadastro de novos autores, com validações apropriadas. ✨
- **Obter Autor por ID**: Recuperação dos dados de um autor específico utilizando seu ID único. 🔍
- **Atualizar Autor**: Atualização dos dados do autor existente, com validação de dados e consistência. 🔄
- **Deletar Autor**: Exclusão de autor do sistema, com verificações de dependência. 🗑️
- **Buscar Autores**: Pesquisa dinâmica de autores por nome e nacionalidade, permitindo consultas filtradas. 🔎

### 3. **Operações CRUD para Livros** 📚📖

- **Criar Livro**: Cadastro de novos livros, incluindo detalhes como título, ISBN, preço, autor e gênero. ✨
- **Obter Livro por ID**: Recuperação dos detalhes de um livro específico pelo ID. 🔍
- **Atualizar Livro**: Atualização dos dados de um livro existente, incluindo informações de publicação e autor. 🔄
- **Deletar Livro**: Exclusão de livro do sistema com verificações de dependência. 🗑️
- **Buscar Livros**: Pesquisa avançada de livros com base em parâmetros como ISBN, título, autor, gênero e ano de publicação. 🔎

### 4. **Segurança e Acesso** 🔐

- **Controle de Acesso com Spring Security**: Definição de regras de segurança e permissões para operações específicas. 🔒
- **Papéis de Usuário**: Controle de acesso baseado em papéis (ex: OPERADOR, GERENTE), permitindo diferentes níveis de autorização para as operações. 👤

### 5. **Swagger e Documentação da API** 📜

- **Swagger UI**: Interface de documentação interativa da API, permitindo testar as rotas diretamente na interface. 🖥️
- **OpenAPI**: Documentação detalhada da API conforme os padrões OpenAPI, com especificações claras dos endpoints, parâmetros e respostas. 📑

### 6. **Tratamento de Erros** ⚠️

- **Erros HTTP Apropriados**: Respostas HTTP apropriadas para cada tipo de erro, incluindo códigos de status como 404 (Não Encontrado), 400 (Bad Request), 422 (Erro de Validação), entre outros. 🚫
- **Mensagens de Erro Detalhadas**: Respostas claras e explicativas para facilitar a identificação e resolução de problemas. 📉

### 7. **Monitoramento e Observabilidade** 📊

- **Spring Actuator**: Monitoramento da saúde e métricas da aplicação. 🩺
- **Spring Observer**: Monitoramento de eventos e fluxos da aplicação, permitindo um maior controle sobre o comportamento do sistema. 📈
"""

## 🔑 Autenticação

A API requer autenticação via OAuth2 para manipular entidades como livros, autores, clientes e usuários. 
- Após autenticação, um **token JWT** é gerado e válido por 1 hora.
- Quando o token expira, um **refresh token** é utilizado para gerar um novo token automaticamente.

## 📖 Endpoints da API

### 🖊️ Autores

- **POST /autores** - Cadastra um novo autor *(Requer papel `GERENTE`)*
- **GET /autores/{id}** - Obtém detalhes de um autor *(Requer `OPERADOR` ou `GERENTE`)*
- **DELETE /autores/{id}** - Deleta um autor *(Requer `GERENTE`)*
- **GET /autores** - Pesquisa autores por parâmetros *(Requer `OPERADOR` ou `GERENTE`)*
- **PUT /autores/{id}** - Atualiza os dados de um autor *(Requer `GERENTE`)*

### 👤 Clientes

- **POST /clients** - Registra um novo cliente *(Requer `GERENTE`)*

### 📚 Livros

- **POST /livros** - Cadastra um novo livro *(Requer `OPERADOR` ou `GERENTE`)*
- **GET /livros/{id}** - Obtém detalhes de um livro *(Requer `OPERADOR` ou `GERENTE`)*
- **DELETE /livros/{id}** - Deleta um livro *(Requer `OPERADOR` ou `GERENTE`)*
- **GET /livros** - Pesquisa livros por parâmetros *(Requer `OPERADOR` ou `GERENTE`)*
- **PUT /livros/{id}** - Atualiza os dados de um livro *(Requer `OPERADOR` ou `GERENTE`)*

### 🔐 Usuários

- **POST /usuarios** - Cadastra um novo usuário

### 🔑 Autenticação

- **GET /login** - Página de login
- **GET /** - Página inicial (exibe o nome do usuário autenticado)
- **GET /authorized?code=CODE** - Exibe o código de autorização OAuth2

## 📜 Licença

Este projeto está licenciado sob a **Licença MIT**. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.

---

Feito por Cauã Farias 🚀
