<script>
	export let addPost
  let author = '';
  let post = '';
 
function sendAddPost(){
	addPost(author, post)
	author = '';
  post = '';
}

	
</script>


<h3>Add Post</h3>
<div class="form-control">
  <label for="author"  class="label">
		<span class="label-text">Author</span>
  </label>
  <input bind:value="{author}" name="author" type="text" placeholder="username" class="input input-bordered " />
	<label for="post" class="label">
		<span class="label-text">Post</span>
	</label>
	<textarea bind:value="{post}" name="post" class="textarea textarea-primary" placeholder="Quote"></textarea>
	<button on:click="{sendAddPost}" class="btn btn-secondary mt-4 w-80">Submit</button> 

</div>