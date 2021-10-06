<script>
  let todos = [];
  function addTodo() {
    todos = [...todos, ""];
  }
  function remove(index) {
    todos = [...todos.slice(0, index), ...todos.slice(index + 1)];
  }
</script>

<h1>Todos</h1>

{#each todos as todo, index}
  <input bind:value={todos[index]} /><button on:click={() => remove(index)}
    >X</button
  >
{/each}
<button on:click={addTodo}>Add</button>
