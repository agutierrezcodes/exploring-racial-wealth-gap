<script>
  import SubsectionCard from "../lib/SubsectionCard.svelte";
  import "highcharts/modules/exporting";
  import ObservedArticleText from "../lib/ObservedArticleText.svelte";
  import { fade } from "svelte/transition";

  const subheader = "Conclusion";
  const subtitle = "Tying it all together";
  let conclusion = $state(true);

  const options = {
    threshold: 0.01,
  };

  const removeConclusionCallback = (entries, observer) => {
    entries.forEach((entry) => {
      const elem = entry.target;

      if (entry.intersectionRatio >= 0.01) {
        conclusion = true;
      } else if (entry.intersectionRatio < 0.01) {
        conclusion = false;
      }
    });
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
      <ObservedArticleText callback={removeConclusionCallback} {options}>
        {#if conclusion}
          <h3 class="learning" transition:fade={{ delay: 50, duration: 1000 }}>
            What can we learn from this?
          </h3>
        {/if}
      </ObservedArticleText>

      <div class="notes">
        <div>
          <h3>
            <!-- The racial wealth gap contributes to the gap in higher
                educational achievement. Higher education increases income
                level. Lower income inhibits the likelihood of homeownership and
                as a result, decreases the possibility of passing down property
                to descendants.  -->

            Based on our findings, it appears that we have uncovered a vicious
            cycle that the racial wealth gap fuels: those with lower wealth are
            less likely to obtain a higher education. Additionally, lack of
            higher education renders a person less likely to advance to a higher
            income level. Finally, people with lower income are less likely to
            own a home (REMEMBER: homeownership is also one of the primary ways
            in which generational wealth is built). This implies that a person's
            descendents will be faced with many of the same problems they faced.

            <br />
            <br />

            And the cycle continues, on and on.
          </h3>
        </div>
      </div>

      <div class="action">
        <h4>So, if it were up to you, what would you do?</h4>

        <br />

        <div class="button-section">
          <a
            href="https://inequality.org/article/ten-solutions-bridge-racial-wealth-divide/"
            target="_blank"><button>Do <em>something</em></button></a
          >

          <button id="backtoTop" onclick={scrollToTop}
            >continue the cycle</button
          >
        </div>
      </div>
    </div>
  </div>
</main>

<style>
  .conclusionSection {
    margin-top: 50rem;

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
    padding-bottom: 3rem;
  }

  div.homeIntroSection h2,
  .challenge {
    font-family: "Cinzel";
    font-style: italic;
    font-size: 32px;
    text-align: center;
  }

  .learning,
  h4 {
    font-family: "Cinzel";
    font-style: italic;
    font-size: 32px;
    text-align: center;
    font-weight: 600;

    padding-top: 50rem;
  }

  button {
    font-family: "Cinzel";
    font-style: italic;
    font-size: 32px;
    font-weight: 600;
    background-color: #9a8c98;
    color: #f2e9e4;
    margin: 1rem;

    border: outset #4a4e69 4px;
  }

  .button-section {
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .notes,
  .action {
    height: 100vh;
    background-color: #c9ada7;
    display: block;
    align-items: center;
    justify-content: center;
    /* padding: 30px;
    padding-top: 200px;
    margin-top: 100px; */
    padding: min(20vh, 20rem) 1rem;
  }

  .action {
    padding-bottom: 50rem;
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
