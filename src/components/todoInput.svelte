<script>
    export let todo; 
    export let addTodo;
    console.log(todo)
</script>

<div>
    <input type="text" name="todo" bind:value={todo} placeholder="todo.." />
    <button on:click={addTodo} class="addbtn">add</button>
</div>

<style>
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
</style>