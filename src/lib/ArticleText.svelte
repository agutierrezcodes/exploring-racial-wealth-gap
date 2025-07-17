<script>
  let { children } = $props();
</script>

<div class="article-text">
  <p>
    {@render children()}
  </p>
</div>

<style>
  .article-text {
    margin: 50vh auto;
    width: 50%;
    background-color: #f2e9e4;
    color: #22223b;
    border: solid #22223b 1.5px;
    border-radius: 12px;
    padding-top: 30px;
    padding-bottom: 30px;
    padding-left: 50px;
    padding-right: 50px;
    box-shadow: 12px 12px 14px black;
    font-family: "Times New Roman", Times, serif;
    font-size: 24px;
  }
</style>
