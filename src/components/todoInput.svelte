<script>
    import Button from './Button.svelte'
    export let addTodo;
    export let value;
</script>

<div>
    <input type="text" name="todo" bind:value placeholder="todo.." />
    <Button onclick={addTodo} title="Add" />
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
</style>