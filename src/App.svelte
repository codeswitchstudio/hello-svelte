<script>
  //Component Basics
  let count = 1
  function increment(){
    count++
  }


  //Reactivity
  let number = 1
  function add5(){
    number += 5;
  }

  $: multiple = number*2  //this is the reactive assignment


  //Class binding
  let active = 1;

  function changeActive(activeNum){
    active = activeNum
    console.log(activeNum)
  }



  //Arrays and form
  import data from './data.json'
  import Post from './components/Post.svelte'
  import Form from './components/Form.svelte'
  import Buttonrow from './components/Buttonrow.svelte'



  //Posts
  let posts = data.data

  function addPost(author, post){
    // console.log('author: ', author)
    // console.log('post: ', post)
    const _post = {
      id: posts.length +1, 
      author: author,
      post: post
    }
    posts.push(_post)
    posts = posts

  }
</script>


<main class="flex flex-col justify-center items-center h-screen space-y-4">
  <h2>Component Basics</h2>
  {count}
  <button on:click="{increment}" class="btn btn-primary">Primary</button>

  <h2>Reactivity</h2>

  <p>The number is: {number}</p>

<button on:click="{add5}" class="btn btn-accent">Add Five</button>
<p>The number multiplied by 2 is {multiple}</p>


<h2>Conditional Rendering</h2>

{#if multiple < 50}  
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

<h2>Class binding</h2>
<Buttonrow {active} {changeActive} />

<h2>Form Binding</h2>

<Form addPost = {addPost} /> 

<h2>Template Looping</h2>
<div class="overflow-auto space-y-4 p-4">
  {#each posts.reverse() as post}
  <Post author={post.author} post={post.post} />
  {/each}
</div>




</main>

<style>

</style>
