<script>
  import ArticleText from "../lib/ArticleText.svelte";
  import { fade, fly } from "svelte/transition";
  import ObservedArticleText from "../lib/ObservedArticleText.svelte";
  import Scroller from "../lib/Scroller.svelte";

  let introIsVisible = $state(true);
  let genWealth = $state(false);
  let box1 = $state(false);
  let box2 = $state(false);
  let box3 = $state(false);
  let box4 = $state(false);

  const options = {
    threshold: [0.85, 0.95],
  };

  const setIntroVisibility = (entries, observer) => {
    entries.forEach((entry) => {
      const elem = entry.target;

      if (entry.intersectionRatio >= 0.8) {
        introIsVisible = true;
      } else if (entry.intersectionRatio < 0.8) {
        introIsVisible = false;
      }
    });
  };

  const removeStartTextCallback = (entries, observer) => {
    entries.forEach((entry) => {
      const elem = entry.target;

      if (entry.intersectionRatio >= 0.9) {
        introIsVisible = false;
        genWealth = true;
      } else if (entry.intersectionRatio < 0.9) {
        introIsVisible = true;
        genWealth = false;
      }
    });
  };

  const showBox1 = (entries, observer) => {
    entries.forEach((entry) => {
      const elem = entry.target;

      if (entry.intersectionRatio >= 0.9) {
        box1 = true;
      }
    });
  };

  const showBox2 = (entries, observer) => {
    entries.forEach((entry) => {
      const elem = entry.target;

      if (entry.intersectionRatio >= 0.9) {
        box2 = true;
      } else if (entry.intersectionRatio < 0.9) {
        box2 = false;
      }
    });
  };

  const showBox3 = (entries, observer) => {
    entries.forEach((entry) => {
      const elem = entry.target;

      if (entry.intersectionRatio >= 0.9) {
        box3 = true;
      } else if (entry.intersectionRatio < 0.9) {
        box3 = false;
      }
    });
  };

  const showBox4 = (entries, observer) => {
    entries.forEach((entry) => {
      const elem = entry.target;

      if (entry.intersectionRatio >= 0.9) {
        box4 = true;
      } else if (entry.intersectionRatio < 0.9) {
        box4 = false;
      }
    });
  };
</script>

<div class="introduction-text">
  <ObservedArticleText callback={setIntroVisibility} {options}>
    <div class="start-section">
      {#if introIsVisible}
        <h3 class="text-before-scroll" transition:fade>
          Let's start by defining the term "generational wealth".

          <br />
          <br />

          I promise, it's relevant.
        </h3>
      {/if}
    </div>
  </ObservedArticleText>

  <div transition:fade>
    <Scroller layout="right">
      {#snippet sticky()}
        <ObservedArticleText callback={removeStartTextCallback} {options}>
          {#if genWealth}
            <h3 transition:fade={{ delay: 50, duration: 1000 }}>
              Generational Wealth
            </h3>
          {/if}
        </ObservedArticleText>
      {/snippet}

      {#snippet scrolly()}
        <!-- <ObservedArticleText callback={showBox1} {options}>
        {#if box1}
          <div transition:fade={{ delay: 50, duration: 1000 }}> -->
        <ArticleText>
          <p>
            Generational wealth is simply wealth that is passed down through
            families, from one generation to the next.
          </p>
        </ArticleText>
        <!-- </div>
        {/if}
      </ObservedArticleText> -->

        <!-- <ObservedArticleText callback={showBox2} {options}>
        {#if box2}
          <div transition:fade={{ delay: 50, duration: 1000 }}> -->
        <ArticleText>
          <p>This wealth can come in many forms.</p>
        </ArticleText>
        <!-- </div>
        {/if}
      </ObservedArticleText>

      <ObservedArticleText callback={showBox3} {options}>
        {#if box3}
          <div transition:fade={{ delay: 50, duration: 1000 }}> -->
        <ArticleText>
          <p>
            It can include <a
              href="https://dfpi.ca.gov/news/insights/five-steps-to-building-generational-wealth/"
              target="_blank"
              >cash savings, assets such as real estate, connections, and even
              knowledge</a
            >. This allows the wealthy to give their descendants better
            opportunities in life (essentially, a "step up").
          </p>
        </ArticleText>
        <!-- </div>
        {/if}
      </ObservedArticleText>

      <ObservedArticleText callback={showBox4} {options}>
        {#if box4}
          <div transition:fade={{ delay: 50, duration: 1000 }}> -->
        <ArticleText>
          <p>
            Now that we understand the overall concept of generational wealth,
            let us take a look at the racial wealth gap in the United States,
            consider how generational wealth may be a factor, and examine the
            impact of this gap.
          </p>
        </ArticleText>
        <!-- </div>
        {/if}
      </ObservedArticleText> -->
      {/snippet}
    </Scroller>
  </div>
</div>

<style>
  .introduction-text p {
    font-family: "Maitree";
    font-style: normal;
    font-weight: 300;
  }
  .introduction-text {
    color: #22223b;
    margin-top: 50rem;
    margin-bottom: 50rem;
    padding-top: 50rem;
    padding-bottom: 50rem;
    background-color: #c9ada7;

    box-shadow: 16px 16px 12px #22223b;
  }

  h3 {
    font-family: "Cinzel";
    font-style: italic;
    font-size: 32px;
    text-align: center;
  }

  .start-section {
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
    padding: 3rem;
    box-sizing: border-box;
  }

  a {
    color: #9a8c98;
  }
</style>
