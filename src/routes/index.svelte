<script context="module">
  import axios from "axios";

  export function preload({ params, query }) {
    return axios
      .get("https://jsonplaceholder.typicode.com/todos/1")
      .then(response => {
        return {
          posts: response.data
        }
      });
  }
</script>

<script>
  export let posts;

  console.log(posts);
</script>

<style>
  h1,
  figure,
  p {
    text-align: center;
    margin: 0 auto;
  }

  h1 {
    font-size: 2.8em;
    text-transform: uppercase;
    font-weight: 700;
    margin: 0 0 0.5em 0;
  }

  figure {
    margin: 0 0 1em 0;
  }

  p {
    margin: 1em auto;
  }

  @media (min-width: 480px) {
    h1 {
      font-size: 4em;
    }
  }
</style>

<svelte:head>
  <title>{posts.title}</title>
</svelte:head>

<h1>Great success!</h1>

<figure>
  <figcaption>HIGH FIVE!</figcaption>
</figure>

<p>
  <strong>
    Try editing this file (src/routes/index.svelte) to test live reloading.... {posts.title}
  </strong>
</p>
