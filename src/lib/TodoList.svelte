<script>
  let { todoItems = [], deleteTodo } = $props();
</script>

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
          {#if deleteTodo}
            <td>
              <button class="button" onclick={() => deleteTodo(todo._id)}>Delete</button>
            </td>
          {/if}
        </tr>
      {/each}
    </tbody>
  </table>
</div>
