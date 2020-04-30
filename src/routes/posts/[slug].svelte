<script>
  import { stores } from "@sapper/app";
  import { onMount, afterUpdate } from "svelte";
  import Post from "../../components/Post.svelte";

  let { page } = stores();
  let params = $page.params;
  let post;

  page.subscribe(value => {
    params = value.params;
    updatePost(params.slug);
  });

  onMount(() => {
    if (window.MathJax) {
      window.MathJax.Hub.Config({
        tex2jax: {
          inlineMath: [["$", "$"], ["(", ")"]],
          displayMath: [["$$", "$$"], ["[", "]"]],
          processEscapes: true,
          processEnvironments: true
        },
        displayAlign: "center",
        "HTML-CSS": {
          styles: { ".MathJax_Display": { margin: 0 } },
          linebreaks: { automatic: true }
        },
        SVG: {
          scale: 100
        }
      });
    }

    updatePost(params.slug);
  });

  function renderArticle() {
    if (post) {
      document.getElementById("output").innerHTML = post.body;

      if (window.MathJax) {
        window.MathJax.Hub.Queue(["Typeset", window.MathJax.Hub, "output"]);
      }
    }
  }

  function updatePost(postID) {
    let db = firebase.firestore();
    const postRef = db.collection("posts").doc(postID);
    postRef.get().then(function(doc) {
      if (doc.exists) {
        post = doc.data();
        renderArticle();
      }
    });
  }

  function date(timestamp) {
    let date = new Date(timestamp * 1000);
    let month = date.getMonth();
    let months = [
      "January",
      "February",
      "March",
      "April",
      "May",
      "June",
      "July",
      "August",
      "September",
      "October",
      "November",
      "December"
    ];
    month = months[month];
    date = `${month} ${date.getDate()}, ${date.getFullYear()}`;
    return date;
  }
</script>

<style>
  article {
    width: 100%;
    max-width: 50rem;
    margin-bottom: 5rem;
    padding: 0 1rem 5rem 0;
  }

  header {
    display: flex;
    flex-flow: column;
    align-items: flex-start;
    padding-bottom: 1rem;
    margin-bottom: 1rem;
    width: 100%;
    border-bottom: 1px #d6d9dc solid;
  }

  .date {
    font-weight: 300;
    color: #656462;
  }

  .video-container {
    position: relative;
    width: 100%;
    padding-bottom: 56.25%;
    height: 0;
    margin-bottom: 2rem;
  }

  .video-container iframe {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
  }

  .video-container-limiter {
    width: 100%;
    max-width: 80rem;
  }
</style>

{#if post}
  <div class="video-container-limiter">
    <div class="video-container">
      <iframe src={post.video} frameborder="0" title="video" class="video" />
    </div>
  </div>
  <article id="post">
    <header>
      <h1>{post.title}</h1>
      <span class="date">{date(post.published.seconds)}</span>
    </header>

    <div id="output" />
  </article>
{/if}
