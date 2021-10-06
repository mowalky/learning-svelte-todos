<script>
  let todos = [];
  let key;

  // enable 'Add' button
  $: enableAdd = todos.length > 0 && !todos[todos.length - 1];

  function addTodo() {
    todos = [...todos, ""];
  }
  function remove(index) {
    todos = [...todos.slice(0, index), ...todos.slice(index + 1)];
  }
  function focus(el) {
    el.focus();
  }
  // catch enter key - auto add todo
  function handleKeydown(event) {
    key = event.key;
    if (key == "Enter") addTodo();
  }
</script>

<svelte:window on:keydown={handleKeydown} />
<div class="app">
  <h1>Todos</h1>

  {#each todos as todo, index}
    <input use:focus bind:value={todos[index]} /><button
      on:click={() => remove(index)}>X</button
    ><br />
  {/each}
  <button disabled={enableAdd} on:click={addTodo}>Add</button>
</div>

<style>
  .app {
    text-align: center;
  }
</style>
