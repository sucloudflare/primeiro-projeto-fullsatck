<h1>Uso do Axios no Frontend</h1>
<p>No projeto, o Axios é utilizado para realizar requisições HTTP ao backend. Aqui está um exemplo de como isso é feito para adicionar uma nova tarefa à lista:</p>

<pre><code>import React, { useState, useEffect } from 'react';
import axios from 'axios';

function Todo() {
  const [todos, setTodos] = useState([]); // Estado para armazenar tarefas
  const [task, setTask] = useState(''); // Estado para armazenar o texto da nova tarefa

  // Função para buscar tarefas do backend
  const fetchTodos = async () => {
    try {
      const response = await axios.get('http://localhost:8080/api/todos');
      setTodos(response.data); // Atualiza o estado com os dados recebidos
    } catch (error) {
      console.error('Erro ao buscar tarefas:', error);
    }
  };

  // Chama a função quando o componente é montado
  useEffect(() => {
    fetchTodos();
  }, []);

  // Função para adicionar uma nova tarefa
  const addTodo = async () => {
    if (task.trim() !== '') {
      try {
        await axios.post('http://localhost:8080/api/todos', { name: task });
        setTask(''); // Limpa o campo de input
        fetchTodos(); // Atualiza a lista de tarefas após adicionar
      } catch (error) {
        console.error('Erro ao adicionar tarefa:', error);
      }
    }
  };

  return (
    &lt;div&gt;
      &lt;input
        type="text"
        value={task}
        onChange={(e) =&gt; setTask(e.target.value)}
        placeholder="Digite uma nova tarefa"
      /&gt;
      &lt;button onClick={addTodo}&gt;Adicionar&lt;/button&gt;
      &lt;ul&gt;
        {todos.map((todo, index) =&gt; (
          &lt;li key={index}&gt;{todo.name}&lt;/li&gt;
        ))}
      &lt;/ul&gt;
    &lt;/div&gt;
  );
}

export default Todo;
</code></pre>

<h2>Explicação do Código</h2>
<p><strong>Importação do Axios:</strong> A biblioteca Axios é importada para que possamos usá-la para fazer as requisições HTTP.</p>
<p><strong>Estado do Componente:</strong></p>
<ul>
    <li><strong>todos:</strong> Armazena a lista de tarefas.</li>
    <li><strong>task:</strong> Armazena o texto da nova tarefa que o usuário deseja adicionar.</li>
</ul>
<p><strong>Buscar Tarefas (fetchTodos):</strong></p>
<ul>
    <li>A função fetchTodos faz uma requisição GET para o endpoint /api/todos.</li>
    <li>Quando a resposta é recebida, o estado todos é atualizado com os dados retornados do backend.</li>
</ul>
<p><strong>Adicionar Tarefa (addTodo):</strong></p>
<ul>
    <li>A função addTodo é chamada quando o botão "Adicionar" é clicado.</li>
    <li>Ela verifica se o campo task não está vazio e faz uma requisição POST para o endpoint /api/todos, enviando o nome da tarefa no corpo da requisição.</li>
    <li>Após a adição, o campo de entrada é limpo e a lista de tarefas é atualizada chamando fetchTodos() novamente.</li>
</ul>

<h2>Integração com o Backend</h2>
<p>No backend, o Spring Boot é responsável por receber as requisições feitas pelo Axios e interagir com o banco de dados. Aqui está um exemplo do código do controlador Spring Boot:</p>

<pre><code>@RestController
@RequestMapping("/api/todos")
public class TodoController {

    @Autowired
    private TodoService todoService; // Serviço que interage com o repositório

    @GetMapping
    public List<Todo> getAllTodos() {
        return todoService.getAllTodos(); // Retorna todas as tarefas
    }

    @PostMapping
    public Todo addTodo(@RequestBody Todo todo) {
        return todoService.addTodo(todo); // Adiciona a nova tarefa ao banco de dados
    }
}
</code></pre>

<h2>Explicação do Backend</h2>
<p><strong>Controlador (TodoController):</strong></p>
<ul>
    <li>O controlador é anotado com @RestController, o que o torna um controlador de API REST.</li>
    <li>O @RequestMapping("/api/todos") define a base para os endpoints do controlador.</li>
</ul>
<p><strong>Obter Tarefas (getAllTodos):</strong></p>
<ul>
    <li>O método getAllTodos é chamado quando uma requisição GET é feita para /api/todos.</li>
    <li>Ele retorna a lista de tarefas armazenadas no banco de dados, utilizando um serviço que lida com a lógica de negócios.</li>
</ul>
<p><strong>Adicionar Tarefa (addTodo):</strong></p>
<ul>
    <li>O método addTodo é chamado quando uma requisição POST é feita para /api/todos.</li>
    <li>Ele recebe um objeto Todo do corpo da requisição, que foi enviado pelo Axios, e o serviço o adiciona ao banco de dados.</li>
</ul>

<h2>Interação com o Banco de Dados</h2>
<p>O serviço que o controlador utiliza se comunica com o repositório (usando Spring Data JPA) para salvar e recuperar dados. Um exemplo de repositório seria:</p>

<pre><code>public interface TodoRepository extends JpaRepository<Todo, Long> {
}
</code></pre>

<h2>Resumo</h2>
<ul>
    <li>Axios é utilizado no frontend para enviar e receber dados do backend.</li>
    <li>O Spring Boot processa as requisições e interage com o banco de dados para armazenar as tarefas.</li>
    <li>A integração entre o frontend e o backend permite criar aplicações dinâmicas, onde o usuário pode interagir com a interface enquanto os dados são gerenciados eficientemente no servidor.</li>
    <li>Essa abordagem não só facilita a manutenção do código, mas também oferece uma experiência de usuário rica e interativa.</li>
</ul>
