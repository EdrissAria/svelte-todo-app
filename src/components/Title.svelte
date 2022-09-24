<script>
    export let filter;
</script>

<div class="filter-text"><h1>{filter}</h1></div>

<style>
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
</style>