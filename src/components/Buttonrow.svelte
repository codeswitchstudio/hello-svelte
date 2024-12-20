<script>
	export let active 
	export let changeActive; // Expecting a function passed down from the parent


</script>

<div class="join grid grid-cols-3 p-10">
  <button on:click={() => changeActive(1)} 
    class="join-item btn btn-outline {active === 1 ? 'btn-active': ''}">Click
  </button>
  <button on:click={() => changeActive(2)} 
    class="join-item btn btn-outline {active === 2 ? 'btn-active': ''}">Clickitty
  </button>
  <button on:click={() => changeActive(3)} 
    class="join-item btn btn-outline {active === 3 ? 'btn-active': ''}">Clack
  </button>
</div>