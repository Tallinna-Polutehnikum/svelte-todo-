<script>
  let todos = [
    { id: 1, text: "Learn Svelte" },
    { id: 2, text: "Learn svelte again" },
  ];
  let newTodo = "";

  function addTodo() {
    if (newTodo !== "") {
      todos = [
        ...todos,
        { id: Date.now(), text: newTodo },
      ];
      newTodo = "";
    } else {
      alert("Please enter a todo item");
    }
  }

  function removeTodo(id) {
    todos = todos.filter(
      (todo) => todo.id !== id
    );
  }
</script>

<h1>2DO2DAY</h1>

<input
  bind:value={newTodo}
  on:keydown={(event) =>
    event.key === "Enter" && addTodo()}
/>

{#each todos as todo}
  <div class="list">
    <span style="margin-top: 12px; color: black">
      {todo.text}
    </span>
    <button
      class="removeButton"
      on:click={() => removeTodo(todo.id)}
      >DONE</button
    >
  </div>
{/each}

<style>
  .removeButton {
    color: GRAY;
    font-size: 12px;
    display: flex;
    justify-content: center;
    align-items: center;
    width: 30px;
    height: 30px;
    padding-left: 24px;
    padding-right: 24px;
    border: none;
    background: white;
    margin-top: 6px;
  }
  .removeButton:hover {
    color: green;
  }
  .list {
    padding: 10px;
    border: 0.5px solid gray;
    border-radius: 10px;
    display: flex;
    justify-content: space-between;
    width: 20%;
    margin-top: 10px;
    margin-bottom: 10px;
    margin-left: auto;
    margin-right: auto;
  }
</style>
