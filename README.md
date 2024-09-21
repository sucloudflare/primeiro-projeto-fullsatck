  <h1>Projeto Fullstack Todo List - React & Spring Boot</h1>
        <p>Este é um projeto Fullstack Todo List desenvolvido com <strong>React</strong> no frontend e <strong>Spring Boot</strong> no backend. A aplicação permite que os usuários adicionem, visualizem e removam tarefas de uma lista, com as informações sendo armazenadas no banco de dados através de uma API REST.</p>

   <h2>Índice</h2>
        <ul>
            <li><a href="#visao-geral">Visão Geral</a></li>
            <li><a href="#funcionalidades">Funcionalidades</a></li>
            <li><a href="#tecnologias-utilizadas">Tecnologias Utilizadas</a></li>
            <li><a href="#instalacao">Instalação</a></li>
            <li><a href="#como-o-frontend-e-backend-se-unem">Como o Frontend e Backend se Unem</a></li>
            <li><a href="#estrutura-do-projeto">Estrutura do Projeto</a></li>
            <li><a href="#contribuicoes">Contribuições</a></li>
            <li><a href="#licenca">Licença</a></li>
        </ul>

   <h2 id="visao-geral">Visão Geral</h2>
        <p>O objetivo deste projeto é demonstrar a integração entre um frontend desenvolvido em <strong>React</strong> e um backend em <strong>Spring Boot</strong>, criando uma aplicação funcional e escalável para gerenciar tarefas. O usuário pode interagir com uma interface simples e intuitiva, enquanto o backend lida com o armazenamento de dados e a lógica de negócios.</p>

   <h2 id="funcionalidades">Funcionalidades</h2>
        <ul>
            <li>Adicionar novas tarefas</li>
            <li>Exibir todas as tarefas</li>
            <li>Remover tarefas existentes</li>
            <li>Conexão com banco de dados via API REST</li>
        </ul>

  <h2 id="tecnologias-utilizadas">Tecnologias Utilizadas</h2>

  <h3>Frontend:</h3>
        <ul>
            <li><strong>React</strong>: Biblioteca JavaScript para construção de interfaces de usuário.</li>
            <li><strong>Axios</strong>: Para realizar as requisições HTTP ao backend.</li>
            <li><strong>CSS</strong>: Estilização da interface do usuário.</li>
        </ul>

   <h3>Backend:</h3>
        <ul>
            <li><strong>Spring Boot</strong>: Framework Java para criação do backend e API REST.</li>
            <li><strong>Hibernate</strong>: ORM para gerenciamento de entidades e conexão com o banco de dados.</li>
            <li><strong>MySQL</strong>: Banco de dados relacional utilizado para armazenar as tarefas.</li>
        </ul>

   <h2 id="instalacao">Instalação</h2>

   <h3>Backend (Spring Boot)</h3>
        <p>Clone o repositório:</p>
        <pre><code>git clone https://github.com/sucloudflare/primeiro-projeto-fullsatck/tree/main
cd primeiro-projeto-fullsatck</code></pre>

   <p>Configure o banco de dados no arquivo <code>application.properties</code>:</p>
  <pre><code>spring.datasource.url=jdbc:mysql://localhost:3306/todo_db
spring.datasource.username=seu_usuario
spring.datasource.password=sua_senha
spring.jpa.hibernate.ddl-auto=update</code></pre>

   <p>Compile e execute o projeto Spring Boot:</p>
        <pre><code>mvn spring-boot:run</code></pre>
        <p>O backend estará rodando em <code>http://localhost:8080</code>.</p>

  <h3>Frontend (React)</h3>
        <p>Acesse a pasta do frontend:</p>
        <pre><code>cd frontend</code></pre>

   <p>Instale as dependências:</p>
        <pre><code>npm install</code></pre>

   <p>Execute o servidor de desenvolvimento React:</p>
        <pre><code>npm start</code></pre>

   <p>Acesse a aplicação em <code>http://localhost:3000</code>.</p>

   <h2 id="como-o-frontend-e-backend-se-unem">Como o Frontend e Backend se Unem</h2>
        <p>O <strong>frontend</strong> e o <strong>backend</strong> são conectados via requisições HTTP utilizando o <strong>Axios</strong> no React. O backend em Spring Boot expõe endpoints da API REST, e o frontend consome esses endpoints para realizar operações no banco de dados.</p>

   <h3>Fluxo de Comunicação:</h3>
        <ul>
            <li>O React envia uma requisição via <strong>Axios</strong> para os endpoints do backend (por exemplo, <code>POST /api/todos</code> para adicionar uma tarefa).</li>
            <li>O <strong>Spring Boot</strong> recebe a requisição e manipula os dados no banco de dados utilizando o <strong>Hibernate</strong>.</li>
            <li>O backend retorna a resposta (dados ou status) para o frontend.</li>
            <li>O frontend atualiza a interface de acordo com a resposta recebida.</li>
        </ul>

   <h3>Exemplo de Endpoint:</h3>
        <ul>
            <li><code>GET /api/todos</code>: Retorna a lista de tarefas</li>
            <li><code>POST /api/todos</code>: Adiciona uma nova tarefa</li>
            <li><code>DELETE /api/todos/{id}</code>: Remove uma tarefa pelo ID</li>
        </ul>

   <h2 id="estrutura-do-projeto">Estrutura do Projeto</h2>
     <pre><code>project-root/
├── backend/
│   ├── src/main/java/com/example/todo/
│   ├── src/main/resources/
│   ├── pom.xml
├── frontend/
│   ├── public/
│   ├── src/
│   ├── package.json
│   ├── App.js
│   ├── App.css</code></pre>

  <h2 id="contribuicoes">Contribuições</h2>
        <p>Contribuições são bem-vindas! Sinta-se à vontade para enviar pull requests ou abrir issues para melhorar o projeto.</p>

   <h2 id="licenca">Licença</h2>
        <p>Este projeto está licenciado sob a <strong>MIT License</strong>.</p>
    </div>
