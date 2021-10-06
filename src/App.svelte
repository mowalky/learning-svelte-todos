<script>
  let todos = [];

  function addTodo() {
    todos = [...todos, ""];
  }
  function remove(index) {
    todos = [...todos.slice(0, index), ...todos.slice(index + 1)];
  }
  function focus(el) {
    el.focus();
  }
</script>

<h1>Todos</h1>

{#each todos as todo, index}
  <input use:focus bind:value={todos[index]} /><button
    on:click={() => remove(index)}>X</button
  >
{/each}
<button on:click={addTodo}>Add</button>
