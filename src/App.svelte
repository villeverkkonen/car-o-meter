<script>
  import Speedometer from "./Speedometer.svelte";
  let title = "Autoilumittari";
</script>

<div id="app">
  <h1 id="title">{title}</h1>
  <Speedometer />
</div>

<style>
  :global(html, body) {
    overflow-y: scroll;
  }

  :global(body) {
    background: linear-gradient(117deg, #e8ded0, #fff 95%);
    text-align: center;
    font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
    -webkit-font-smoothing: antialiased;
  }

  :global(.openSans) {
    font-family: "Open Sans", sans-serif;
    color: #c9263f;
  }

  :global(.result) {
    margin: 20px;
  }

  :global(.carPicture) {
    width: 8em;
  }

  #title {
    font-family: "Courier New", Courier, monospace;
    color: #c9263f;
  }
</style>
