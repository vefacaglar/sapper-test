<script context="module">
  import axios from "axios";

  export async function preload({ params, query }) {
    const data = await axios.get(
      `https://jsonplaceholder.typicode.com/posts/${params.id}`
    );

    const comments = await axios.get(
      `https://jsonplaceholder.typicode.com/comments?postId=${params.id}`
    );

    return {
      post: data.data,
      comments: comments.data
    };
  }
</script>

<script>
  export let post;
  export let comments
</script>

<style>
  /*
		By default, CSS is locally scoped to the component,
		and any unused styles are dead-code-eliminated.
		In this page, Svelte can't know which elements are
		going to appear inside the {{{post.html}}} block,
		so we have to use the :global(...) modifier to target
		all elements inside .content
  */
  
  .comments{
    margin-top: 15px;
  }

  .comment-item{
    padding: 5px;
    border: 1px solid black;
    border-radius: 5px;
    margin-bottom: 10px;
  }
</style>

<svelte:head>
  <title>{post.title}</title>
</svelte:head>

<h1>{post.title}</h1>

<!-- <div class="content">
  {@html post.html}
</div> -->

<div>{post.body}</div>

<div class="comments">
  <h5>Comments:</h5>
  {#each comments as comment}
    <div class="comment-item">
      <div class="comment-email">{comment.email}</div>
      <div class="comment-body">
      {comment.body}
      </div>
    </div>
  {/each}
</div>
