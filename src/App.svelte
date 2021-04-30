<script>
  let todos = [
    { key: 0, task: "Mow lawn", done: false },
    { key: 1, task: "Do dishes", done: false },
    { key: 2, task: "Apply to jobs", done: false },
  ];
</script>

<main>
  <div class="row">
    <h1>To-Do List</h1>
  </div>
  <div class="row">
    <ul class="todos">
      {#each todos as todo}
        <li class="todo-row">
          <input class="todo-done" type="checkbox" checked={todo.checked} />
          {todo.task}
        </li>
      {/each}
    </ul>
  </div>
</main>

<style>
  .todo-row {
    padding-bottom: 10px;
  }

  .row {
    width: 100%;
    display: flex;
    justify-content: center;
  }

  main {
    padding: 1em;
    margin: 0 auto;
    width: 600px;
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
    font-family: Roboto, sans-serif;
    background: white;
    border-radius: 5px;
  }
  ul,
  li {
    list-style: none outside none;
    padding-left: 0;
  }
  .todo-done {
    margin-right: 10px;
  }
</style>
