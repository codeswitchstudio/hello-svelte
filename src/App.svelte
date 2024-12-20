<script>
  let count = 1

  function increment(){
    count++
  }

</script>

<main class="flex flex-col justify-center intems-venter h-screen space-y-4">
{count}
<button on:click="{increment}" class="btn btn-primary">Primary</button>
</main>

<style>

</style>
