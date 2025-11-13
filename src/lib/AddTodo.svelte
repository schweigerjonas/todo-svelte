<script>
  let { todoText = $bindable(""), addTodo } = $props();
</script>

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
      <button class="button" onclick={() => addTodo()}>Add todo</button>
    </div>
  </div>
</div>
