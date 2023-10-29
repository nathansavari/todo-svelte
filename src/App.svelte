<script lang="ts">
  let todos = localStorage.getItem("todos") ? JSON.parse(localStorage.getItem("todos") || "null") : []
  let newTodo = ""

  function addTodo() {
    if (newTodo !== "") {
      todos = [...todos, newTodo]
      localStorage.setItem("todos", JSON.stringify(todos))
    }
    newTodo = ""
  }

  function deleteTodo(index: number) {
    todos.splice(index, 1)
    todos = todos
    localStorage.setItem("todos", todos)
  }


</script>

<input bind:value={newTodo} on:change={() => addTodo()}/>
<ul>
  {#each todos as todo, index}
  <div>
    <li>{todo}</li>
    <button on:click={() => deleteTodo(index)}>x</button>
  </div>
  {/each}
</ul>


<style>
  ul {
    padding: 0;
    list-style-type: none;
  }

  div {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 10px;
  }

  li {
    padding: 10px 20px;
    background-color: #f4f4f4;
    border: 1px solid #ddd;
    border-radius: 5px;
    flex-grow: 1;
  }

  button {
    margin-left: 10px;
    background-color: red;
    color: white;
    border: none;
    border-radius: 50%;
    width: 25px;
    height: 25px;
    cursor: pointer;
  }

  button:hover {
    background-color: darkred;
  }
</style>
