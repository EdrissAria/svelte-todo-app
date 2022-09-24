<script>
  // imports
  import Title from "./components/Title.svelte";
  import TodoInput from "./components/todoInput.svelte";
  import TodoCard from "./components/todoCard.svelte";
  import Button from "./components/Button.svelte"  
  // variables and functions
  let todos = [];
  $: todo = "";
  let filter = "all";
  const addTodo = () => {
    if (todo == "") {
      alert("Input Must be filled!");
    } else {
      todos = [
        {
          todo: todo,
          status: false,
        },
        ...todos,
      ];
      todo = "";
    }
  };
  const deleteTodo = (id) => {
    todos.splice(id, 1);
    todos = [...todos];
  };
</script>

<main>
  <Title {filter} />
  <div class="content">
    <TodoInput {addTodo} bind:value={todo} />
    <div>
      {#each todos as todo, index}
        {#if filter == "all"}
          <TodoCard {todo} {deleteTodo} {index} />
        {:else if filter == "completed"}
          {#if todo.status}
            <TodoCard {todo} {deleteTodo} {index} />
          {/if}
        {:else if !todo.status}
          {#if !todo.status}
            <TodoCard {todo} {deleteTodo} {index} />
          {/if}
        {/if}
      {:else}
        <img src="empty.png" alt="empty" class="empty" />
        <h1>No To-dos</h1>
      {/each}
    </div>
    <div class="btn-footer">
      <Button onclick={() => (filter = "all")} title="All"/>
      <Button onclick={() => (filter = "completed")} title="Completed"/>
      <Button onclick={() => (filter = "uncompleted")} title="Uncompleted" />
    </div>
  </div>
</main>

<style>
  :root {
    --light: rgb(240, 240, 240);
    --dark: rgb(122, 122, 122);
    --bgGreen: transparent linear-gradient(109deg, #79f5c5 0%, #2dd393 100%);
    --bgBlue: transparent linear-gradient(112deg, #19e7da 0%, #6078ea 100%);
    --bgRed: transparent linear-gradient(112deg, #fe7379 0%, #f54ea1 100%);
    --bgPurple: transparent linear-gradient(112deg, #b374d3 0%, #2b26a7 100%);
    --bgOrange: transparent linear-gradient(112deg, #fec273 0%, #ffa600 100%);
    --shadowGreen: 0 16px 20px #ffceb9;
    --shadowBlue: 0 16px 20px #b9f4ff;
    --shadowRed: 0 16px 20px #f58e75;
    --shadowPurple: 0 16px 20px #f3b9ff;
  }
  .content {
    text-align: center;
    margin: 100px 20px;
    background: transparent linear-gradient(109deg, #79f5c5 0%, #2dd393 100%) 0%
      0% no-repeat padding-box;
    box-shadow: var(--shadowGreen);
    padding: 2rem;
    border-radius: 1rem;
  }
  .content h1 {
    color: var(--light);
    font-family: sans-serif;
  }
  .btn-footer {
    display: flex;
    justify-content: center;
    margin-top: 2rem;
  }  
  .empty {
    width: 300px;
  }
</style>
