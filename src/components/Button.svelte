<script>
    export let onclick; 
    export let title; 
</script>

<button on:click={onclick} class="btn">{title}</button>

<style>
  .btn {
    border: 1px solid rgb(60, 133, 201);
    background: var(--bgBlue);
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
</style>