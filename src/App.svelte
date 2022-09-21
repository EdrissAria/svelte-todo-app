<script>
    import { empty } from "svelte/internal";

  let todos = [];
  let todo = "";
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
  <div class="filter-text"><h1>{filter}</h1></div>
  <div class="content">
    <input type="text" name="todo" bind:value={todo} placeholder="todo.." />
    <button on:click={addTodo} class="addbtn">add</button>
    <div>
      {#each todos as todo, index}
        {#if filter == "all"}
          <div class="todo">
            <p>{todo.todo}</p>
            <div class="btn-content">
              <input type="checkbox" bind:checked={todo.status} />
              <button on:click={() => deleteTodo(index)}>&Cross;</button>
            </div>
          </div>
        {:else if filter == "completed"}
          {#if todo.status}
            <div class="todo">
              <p>{todo.todo}</p>
              <div class="btn-content">
                <input type="checkbox" bind:checked={todo.status} />
                <button on:click={() => deleteTodo(index)}>&Cross;</button>
              </div>
            </div>
          {/if}
        {:else if !todo.status}
          {#if !todo.status}
            <div class="todo">
              <p>{todo.todo}</p>
              <div class="btn-content">
                <input type="checkbox" bind:checked={todo.status} />
                <button on:click={() => deleteTodo(index)}>&Cross;</button>
              </div>
            </div>
          {/if}
        {/if}
      {/each}
    </div>
    <div class="btn-footer">
      <button on:click={() => (filter = "all")} class="btn">All</button>
      <button on:click={() => (filter = "completed")} class="btn"
        >Completed</button
      >
      <button on:click={() => (filter = "uncompleted")} class="btn"
        >Uncompleted</button
      >
    </div>
  </div>
</main>

<style>
  :root {
    --light: rgb(240, 240, 240);
    --dark: rgb(122, 122, 122);
    --bgGreen: transparent linear-gradient(109deg, #79f5c5 0%, #2dd393 100%) 0%
      0% no-repeat padding-box;
    --bgBlue: transparent linear-gradient(112deg, #19e7da 0%, #6078ea 100%);
    --bgRed: transparent linear-gradient(112deg, #fe7379 0%, #f54ea1 100%);
    --bgPurple: transparent linear-gradient(112deg, #b050d1 0%, #2b26a7 100%);
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
  .filter-text {
    position: absolute;
    top: 10px;
    left: 50%;
    transform: translateX(-50%);
    width: 400px;
    height: 140px;
    background: var(--bgOrange);
    border-radius: 1rem;
    z-index: -1;
    box-shadow: var(--bgGreen);
    text-align: center;
  }
  .filter-text h1 {
    font-size: 30pt;
    color: #ffffff;
    font-family: sans-serif;
    text-transform: capitalize;
  }
  input[type="text"] {
    width: 500px;
    padding: 0.7rem 1rem;
    outline: none;
    border: 1px solid rgb(2, 255, 179);
    border-radius: 0.2rem;
    font-size: 1.2rem;
    color: var(--dark);
  }
  input[type="text"]::placeholder {
    color: var(--light);
  }
  input[type="text"]:focus {
    border: 1px solid rgb(17, 236, 116);
  }
  .addbtn {
    border: 1px solid rgb(79, 181, 248);
    background: var(--bgBlue);
    border-radius: 0.2rem;
    padding: 0.7rem 1rem;
    font-size: 1.2rem;
    color: #fff;
    cursor: pointer;
  }
  .addbtn:hover {
    transform: scale(1.01);
  }
  .todo {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-top: 2rem;
    padding: 0.7rem 1rem;
    border-radius: 0.4rem;
    border: 1px solid rgb(165, 59, 236);
    background: var(--bgPurple);
    animation-name: bounce;
    animation-duration: 1s;
    animation-timing-function: linear;
  }
  @keyframes bounce {
    0% {
      -webkit-transform: scale3d(1, 1, 1);
      transform: scale3d(1, 1, 1);
    }
    50% {
      -webkit-transform: scale3d(1.01, 1.01, 1.01);
      transform: scale3d(1.01, 1.01, 1.01);
    }
    100% {
      -webkit-transform: scale3d(1, 1, 1);
      transform: scale3d(1, 1, 1);
    }
  }
  .todo p {
    font-size: 1.6rem;
    color: rgba(255, 255, 255, 0.959);
    font-family: sans-serif;
  }
  .btn-content {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  .todo input {
    position: relative;
    transition: 0.5s;
    width: 50px;
    height: 50px;
    margin-right: 0.7rem;
    border-radius: 0.7rem;
    background: var(--light);
    appearance: none;
    cursor: pointer;
    border: 1px solid rgb(87, 166, 255);
  }
  .todo input::before {
    position: absolute;
    left: 10px;
    top: 30%;
    height: 50%;
    width: 5px;
    background-color: var(--light);
    content: "";
    transform: translateX(10px) rotate(-45deg);
    transform-origin: left bottom;
  }
  .todo input::after {
    position: absolute;
    left: 10px;
    bottom: 10px;
    height: 5px;
    width: 40px;
    background-color: var(--light);
    content: "";
    transform: translateX(10px) rotate(-45deg);
    transform-origin: left bottom;
  }
  .todo input:checked {
    background: var(--bgBlue);
  }
  .todo button {
    transition: 0.5s;
    width: 50px;
    height: 50px;
    color: #fff;
    font-size: 2.5rem;
    border-radius: 0.7rem;
    background: var(--bgRed);
    cursor: pointer;
    border: 1px solid rgb(250, 90, 61);
  }
  .btn-footer {
    display: flex;
    justify-content: center;
    margin-top: 2rem;
  }
  .btn {
    border: 1px solid rgb(245, 213, 30);
    background: var(--bgOrange);
    border-radius: 0.2rem;
    padding: 0.7rem 1rem;
    font-size: 1.2rem;
    color: #fff;
    cursor: pointer;
    margin-left: 1rem;
    transition: 0.5s;
  }
  .btn:hover {
    transform: scale3d(1.01, 1.01, 1.01);
  }

  /* Media Query */
  @media (max-width: 991.98px) {
    input[type="text"] {
      width: 300px;
    }
    .filter-text {
      width: 200px;
    }
    .filter-text h1 {
      font-size: 24pt;
    }
  }
  @media (max-width: 467px) {
    input[type="text"] {
      width: 190px;
      font-size: 1rem;
      padding: 0.5rem 0.3rem;
    }
    .addbtn {
      padding: 0.5rem 0.3rem;
      font-size: 1rem;
    }
    .filter-text {
      width: 200px;
    }
    .filter-text h1 {
      font-size: 20pt;
    }
    .content {
      padding: 10px;
    }
    .btn {
      font-size: 0.8rem;
      padding: 0.5rem 0.3rem;
    }
  }
</style>
