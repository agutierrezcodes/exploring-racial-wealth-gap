<script>
  import Scroller from "../lib/Scroller.svelte";
  import ArticleText from "../lib/ArticleText.svelte";
</script>

<div>
  <Scroller layout="right">
    {#snippet sticky()}
      <ArticleText>intro text here</ArticleText>
    {/snippet}

    {#snippet scrolly()}
      <ArticleText>Sample text here</ArticleText>
      <ArticleText>conclusion text here</ArticleText>
    {/snippet}
  </Scroller>
</div>
