<script>
    import TodoCard from "./todoCard.svelte";
    export let todos;
    export let filter;
</script>

<div>
    {#each todos as todo, index}
        {#if filter == "all"}
            <TodoCard {index} {todo}/>
        {:else if filter == "completed"}
            {#if todo.status}
                <TodoCard {index} {todo}/>
            {/if}
        {:else if !todo.status}
            {#if !todo.status}
                <TodoCard {index} {todo}/>
            {/if}
        {/if}
    {:else}
        <img src="empty.png" alt="empty" class="empty" />
        <h1>No To-dos</h1>
    {/each}
</div>

<style>
    h1 {
        color: var(--light);
        font-family: sans-serif;
    }
    .empty {
        width: 300px;
    }
</style>
