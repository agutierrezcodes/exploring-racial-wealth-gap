<script>
  import TitleCard from "../lib/TitleCard.svelte";

  const title = "IS IT TIME TO BRIDGE THE GENERATIONAL WEALTH GAP?";
  const subtitle =
    "An exploration of the effects of the generational wealth gap in America";
</script>

<main>
  <TitleCard {title} {subtitle} />
  <h4>Scroll to learn more</h4>
  <img src="" alt="Arrow image pointing down" />
</main>

<style>
  h4 {
    color: #f2e9e4;
    opacity: 80%;
    text-align: center;
    font-size: 28px;
    padding-bottom: 50px;
    font-family: "SpaceMono";
    font-style: italic;
  }
  img {
    /* make sure img is centered and responsive*/
    display: block;
    margin-right: auto;
    margin-left: auto;
    text-align: center;
    height: auto;
    max-width: 100%;
  }
</style>
