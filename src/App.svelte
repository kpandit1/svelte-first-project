<script>
  let todos = [
    { key: 0, task: "Mow lawn", done: false },
    { key: 1, task: "Do dishes", done: false },
    { key: 2, task: "Apply to jobs", done: true },
  ];
  let newTodoInput = "";

  function handleAdd() {
    if (newTodoInput === "") {
      return;
    }
    todos = [
      ...todos,
      {
        key: todos.length,
        task: newTodoInput,
        done: false,
      },
    ];
    newTodoInput = "";
  }
  let showDone = true;

  $: filteredTodos = todos.filter((todo) => !todo.done);
  $: displayTodos = showDone ? todos : filteredTodos;
</script>

<main>
  <div class="row">
    <h1>To-Do List</h1>
  </div>
  <div class="row">
    <form on:submit|preventDefault={handleAdd}>
      <input class="add-todo" type="text" bind:value={newTodoInput} />
      <button type="submit" class="btn">+ ADD</button>
    </form>
  </div>
  <div class="row">
    <ul class="todos">
      {#each displayTodos as todo, i}
        <li class="todo-row" class:done={todo.done}>
          <input
            class="todo-done"
            type="checkbox"
            checked={todo.done}
            on:click={() => (todos[i].done = !todos[i].done)}
          />
          {todo.task}
        </li>
      {/each}
    </ul>
  </div>
  <div class="row">
    <button on:click={() => (showDone = !showDone)}
      >{showDone ? "Hide" : "Show"} done</button
    >
  </div>
</main>

<style>
  .todo-row {
    padding-bottom: 10px;
  }

  .add-todo {
    width: 300px;
    margin-right: 4px;
  }
  .row {
    width: 100%;
    display: flex;
    justify-content: center;
  }

  .done {
    text-decoration: line-through;
  }

  main {
    padding: 1em;
    margin: 0 auto;
    width: 600px;
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
    font-family: Roboto, sans-serif;
    background: white;
    border-radius: 5px;
    margin-top: 10px;
  }
  ul,
  li {
    list-style: none outside none;
    padding-left: 0;
  }
  .todo-done {
    margin-right: 10px;
  }
  button {
    cursor: pointer;
  }
</style>
