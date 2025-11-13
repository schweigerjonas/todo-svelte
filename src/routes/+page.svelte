<script>
  import { v4 as uuidv4 } from "uuid";
  import Title from "$lib/Title.svelte";
  import TodoList from "$lib/TodoList.svelte";
  import AddTodo from "$lib/AddTodo.svelte";

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
  <Title title="Todo Components" subtitle="A new approach" />
  <AddTodo bind:todoText {addTodo} />
  <TodoList {todoItems} {deleteTodo} />
  <TodoList todoItems={doneItems} />
</div>
