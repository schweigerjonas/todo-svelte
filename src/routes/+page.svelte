<script>
  let todoText = "";
  let todoItems = $state([]);

  function addTodo() {
    console.log(todoText);
    todoItems.push(todoText);
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
          <th>Task</th>
        </tr>
      </thead>
      <tbody>
        {#each todoItems as todo (todo)}
          <tr>
            <td>{todo}</td>
          </tr>
        {/each}
      </tbody>
    </table>
  </div>
</div>
