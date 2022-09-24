<script>
    export let todo; 
    export let deleteTodo;  
    export let index;
</script>

<div class="todo">
    <p>{todo.todo}</p>
    <div class="btn-content">
        <input type="checkbox" bind:checked={todo.status} />
        <button on:click={() => deleteTodo(index)}>&Cross;</button>
    </div>
</div>

<style>
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
</style>
