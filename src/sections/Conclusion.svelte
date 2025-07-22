<script>
  import SubsectionCard from "../lib/SubsectionCard.svelte";
  import * as Highcharts from "highcharts";
  import "highcharts/modules/exporting";
  import { Chart } from "@highcharts/svelte";
  import Scroller from "../lib/Scroller.svelte";
  import ObservedArticleText from "../lib/ObservedArticleText.svelte";
  import ArticleText from "../lib/ArticleText.svelte";
  import { fade } from "svelte/transition";

  const subheader = "Conclusion";
  const subtitle = "Tying it all together";

  const options = {
    threshold: [0.85, 0.95],
  };

  let homeIntroIsVisible = $state(true);
  let recapIsVisible = $state(true);
  let degreeIsVisible = $state(true);
  let incomeIsVisible = $state(true);

  //credit for scroll to top code: https://stackoverflow.com/questions/58213748/how-to-animate-scroll-to-top-javascript
  function scrollToTop() {
    window.scrollTo({ top: 0, behavior: "smooth" });
  }
</script>

<main>
  <SubsectionCard {subheader} {subtitle} />

  <div class="conclusionSection">
    <div class="conclusionContentSection">
      <h3 class="learning" transition:fade={{ delay: 50, duration: 1000 }}>
        What can we learn from this?
      </h3>

      <div class="notes">
        <h3>
          <!-- The racial wealth gap contributes to the gap in higher
                educational achievement. Higher education increases income
                level. Lower income inhibits the likelihood of homeownership and
                as a result, decreases the possibility of passing down property
                to descendants.  -->

          It is appears from our findings that we have uncovered a vicious cycle
          that the racial wealth gap creates: lower wealth makes it less likely
          that people will obtain a higher education. A lack of higher education
          makes it less likely that people will advance to a higher income
          level. People with lower income are less likely to own a home
          (REMEMBER: homeownership is one of the primary ways in which
          generational wealth is built). Therefore, their descendents will be
          faced with many of the same problems they faced.

          <br />

          And the cycle continues.
        </h3>
      </div>

      <h4>
        Do we want to try to <button>change this?</button> or simply
        <button id="backtoTop" onclick={scrollToTop}>continue the cycle?</button
        >
      </h4>
    </div>
  </div>
</main>

<style>
  .conclusionSection {
    margin-top: 50rem;
    margin-bottom: 50rem;

    box-shadow: 16px 16px 12px #22223b;
    background-color: #4a4e69;
  }

  p,
  h3 {
    font-family: "Maitree";
    font-style: normal;
    font-weight: 300;
  }

  img {
    display: block;
    margin-right: auto;
    margin-left: auto;
    text-align: center;
    max-width: 80%;
  }

  .conclusionContentSection {
    background-color: #c9ada7;

    padding-top: 3rem;
  }

  div.homeIntroSection h2,
  .challenge {
    font-family: "Cinzel";
    font-style: italic;
    font-size: 32px;
    text-align: center;
  }

  .learning {
    font-family: "Cinzel";
    font-style: italic;
    font-size: 32px;
    text-align: center;
    font-weight: 600;

    padding-top: 50rem;
  }

  button {
    font-family: "Maitree";
    font-style: normal;
    font-weight: 300;
  }

  .notes {
    height: 100vh;
    background-color: #c9ada7;
    display: flex;
    align-items: center;
    justify-content: center;
    /* padding: 30px;
    padding-top: 200px;
    margin-top: 100px; */
    padding: min(20vh, 20rem) 1rem;
  }

  div.notes h3 {
    font-style: italic;
    font-size: 26px;
    text-align: center;
    padding: 3.7rem;
    background-color: #9a8c98;
    border: 8px ridge #4a4e69;
    border-radius: 4px;
    margin: 8%;
    box-shadow: 12px 12px 16px black;
    color: #f2e9e4;
  }
</style>
