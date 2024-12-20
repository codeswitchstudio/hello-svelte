<script>
  let count = 1
  function increment(){
    count++
  }

  let number = 1
  function add5(){
    number += 5;
  }

  $: multiple = number*2  //this is the reactive assignment



  //class binding
  let active = 1;

  function changeActive(activeNum){
    active = activeNum
    console.log(activeNum)
  }




  //arrays and form
  import data from './data.json'
  let author = '';
  let post = '';
 
  let posts = data.data


  function addPost(){
    // console.log('author: ', author)
    // console.log('post: ', post)
    const _post = {
      id: posts.length +1, 
      author: author,
      post: post
    }

    posts.push(_post)
    posts = posts

    author = " "
    post = " "

  }
</script>


<main class="flex flex-col justify-center items-center h-screen space-y-4">


<h1>Component Basics</h1>

{count}
<button on:click="{increment}" class="btn btn-primary">Primary</button>


<h1>Reactivity</h1>

<p>The number is: {number}</p>

<button on:click="{add5}" class="btn btn-accent">Add Five</button>
<p>The number multiplied by 2 is {multiple}</p>


<h1>Conditional Rendering</h1>

{#if multiple < 20}  
<div role="alert" class="alert alert-success">
  <svg
    xmlns="http://www.w3.org/2000/svg"
    class="h-6 w-6 shrink-0 stroke-current"
    fill="green"
    viewBox="0 0 24 24">
    <path
      stroke-linecap="round"
      stroke-linejoin="round"
      stroke-width="2"
      d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z" />
  </svg>
  <span>Looks good!</span>
</div>
{:else}  
<div role="alert" class="alert alert-error">
  <svg
    xmlns="http://www.w3.org/2000/svg"
    class="h-6 w-6 shrink-0 stroke-current"
    fill="red"
    viewBox="0 0 24 24">
    <path
      stroke-linecap="round"
      stroke-linejoin="round"
      stroke-width="2"
      d="M10 14l2-2m0 0l2-2m-2 2l-2-2m2 2l2 2m7-2a9 9 0 11-18 0 9 9 0 0118 0z" />
  </svg>
  <span>Your number is too high!</span>
</div>

{/if}

<h1>Class binding</h1>
<div class="join p-10">
  <button on:click={() => changeActive(1)} 
    class="join-item btn btn-info {active === 1 ? 'btn-active': ''}">Click
  </button>
  <button on:click={() => changeActive(2)} 
    class="join-item btn btn-warning {active === 2 ? 'btn-active': ''}">Clickitty
  </button>
  <button on:click={() => changeActive(3)} 
    class="join-item btn btn-success {active === 3 ? 'btn-active': ''}">Clack
  </button>
</div>

<h1>Form Binding</h1>
<h2>Add Post</h2>
<div class="form-control">
  <label for="author"  class="label">
    <span class="label-text">Author</span>
  </label>
  <input bind:value="{author}" name="author" type="text" placeholder="username" class="input input-bordered " />

<label for="post" class="label">
  <span class="label-text">Post</span>
</label>

<textarea bind:value="{post}" name="post" class="textarea textarea-primary" placeholder="Quote"></textarea>
</div>
<button on:click="{addPost}" class="btn btn-secondary mt-4 w-80">Submit</button> 

<h1>Template Looping</h1>
<div class="overflow-auto space-y-4 p-4">
  {#each posts.reverse() as post}
  <div class="card bordered w-80 shadow-xl bg-primary">
    <div class="card-body">
      <h2 class="card-title">{post.author}</h2>
      <p>{post.post}</p>
    </div>
  
  </div>
  {/each}
</div>




</main>

<style>

</style>
