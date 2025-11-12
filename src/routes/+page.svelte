<script>
  import { v4 as uuidv4 } from "uuid";
  let todoText = $state("");
  let todoItems = $state([]);
  let doneItems = $state([]);

  function addTodo() {
    const todo = {
      _id: uuidv4(),
      text: todoText,
      date: new Date().toLocaleString("en-IE")
    };

    todoItems.push(todo);
    todoText = "";
  }

  function deleteTodo(id) {
    doneItems.push(todoItems.find((todo) => todo._id === id));
    todoItems = todoItems.filter((todo) => todo._id !== id);
  }
</script>

<div class="container">
  <div class="box has-centered-text">
    <div class="title">Simple Todo List</div>
    <div class="subtitle">Fun things to do</div>
  </div>

  <div class="section box">
    <div class="field is-horizontal">
      <div class="field-label is-normal">
        <label for="todo" class="label">What should I do?</label>
      </div>
      <div class="field-body">
        <div class="field">
          <p class="control">
            <input
              id="todo"
              class="input"
              type="text"
              placeholder="Type something..."
              bind:value={todoText}
            />
          </p>
        </div>
        <div class="button" onclick={() => addTodo()}>Add todo</div>
      </div>
    </div>
  </div>

  <div class="section box">
    <div class="title is-6">Things yet to do</div>
    <table class="table is-fullwidth">
      <thead>
        <tr>
          <th>TASK</th>
          <th>DATE</th>
          <th></th>
        </tr>
      </thead>
      <tbody>
        {#each todoItems as todo (todo._id)}
          <tr>
            <td>{todo.text}</td>
            <td>{todo.date}</td>
            <td>
              <button class="button" onclick={() => deleteTodo(todo._id)}>Delete</button>
            </td>
          </tr>
        {/each}
      </tbody>
    </table>
  </div>

  <div class="section box">
    <div class="title is-6">Things done</div>
    <table class="table is-fullwidth">
      <thead>
        <tr>
          <th>TASK</th>
          <th>DATE</th>
        </tr>
      </thead>
      <tbody>
        {#each doneItems as todo (todo._id)}
          <tr>
            <td>{todo.text}</td>
            <td>{todo.date}</td>
          </tr>
        {/each}
      </tbody>
    </table>
  </div>
</div>
