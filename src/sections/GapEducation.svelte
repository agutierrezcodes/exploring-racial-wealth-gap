<script>
  import SubsectionCard from "../lib/SubsectionCard.svelte";
  import * as Highcharts from "highcharts";
  import "highcharts/modules/exporting";
  import { Chart } from "@highcharts/svelte";
  import Scroller from "../lib/Scroller.svelte";
  import ObservedArticleText from "../lib/ObservedArticleText.svelte";
  import ArticleText from "../lib/ArticleText.svelte";
  import { fade } from "svelte/transition";

  const subheader = "THE IMPACT OF THE GAP";
  const subtitle = "Education";

  const options = {
    threshold: [0.85, 0.95],
  };

  let edIntroIsVisible = $state(true);
  let degreeIsVisible = $state(true);
  let incomeIsVisible = $state(true);

  const setIncomeVisibility = (entries, observer) => {
    entries.forEach((entry) => {
      const elem = entry.target;

      if (entry.intersectionRatio >= 0.9) {
        incomeIsVisible = true;
      } else if (entry.intersectionRatio < 0.9) {
        incomeIsVisible = false;
      }
    });
  };

  const setDegreeVisibility = (entries, observer) => {
    entries.forEach((entry) => {
      const elem = entry.target;

      if (entry.intersectionRatio >= 0.9) {
        degreeIsVisible = true;
      } else if (entry.intersectionRatio < 0.9) {
        degreeIsVisible = false;
      }
    });
  };

  const setEdIntroVisibility = (entries, observer) => {
    entries.forEach((entry) => {
      const elem = entry.target;

      if (entry.intersectionRatio >= 0.9) {
        edIntroIsVisible = true;
      } else if (entry.intersectionRatio < 0.9) {
        edIntroIsVisible = false;
      }
    });
  };
</script>

<main>
  <SubsectionCard {subheader} {subtitle} />

  <div class="gapEdSection">
    <Scroller layout="right">
      {#snippet sticky()}
        <div class="edIntroSection">
          <ObservedArticleText callback={setEdIntroVisibility} {options}>
            <div class="start-section">
              <!-- TODO: fix stuttering with fade transition -->
              {#if edIntroIsVisible}
                <h3 class="text-before-scroll" transition:fade>
                  Generational wealth does not just influence finances. There is
                  a documented positive relationship (INCLUDE HYPERLINK) between
                  wealth and high educational achievement (attending
                  college/achieving a bachelor's degree or higher).
                </h3>
              {/if}
            </div>
          </ObservedArticleText>
        </div>
      {/snippet}

      {#snippet scrolly()}
        <!-- <ObservedArticleText callback={() => {}} {options}> -->
        <div>
          <ArticleText>
            <p>
              The following graph summarizes part of <a
                href="https://www.urban.org/sites/default/files/publication/89976/wealth_and_education_3.pdf"
                target="_blank">Braga, et al's</a
              > research, who found that “Young people from high-wealth families
              (wealth above roughly $223,500) are more than one and a half times
              as likely to complete at least two or four years of college by age
              25 as those in low-wealth families (wealth below $2,000).(1) High-wealth
              youth have a 70 percent chance of completing at least two years and
              a 43 percent chance of completing at least four years of college. Similar
              young people in low-wealth families have only a 41 percent chance of
              completing at least two years and a 24 percent chance of completing
              at least four years. ”
            </p>
          </ArticleText>

          <div>
            <a
              href="https://www.urban.org/sites/default/files/publication/89976/wealth_and_education_3.pdf"
              target="_blank"
              ><img
                class="wealthCollegeImage"
                src="wealth-college.png"
                alt="Graph that shows "
              /></a
            >
          </div>
        </div>
        <!-- </ObservedArticleText> -->
      {/snippet}
    </Scroller>

    <Scroller layout="left">
      {#snippet sticky()}
        <div class="degreeAttainSection">
          <ObservedArticleText callback={setDegreeVisibility} {options}>
            <div class="start-section">
              <!-- TODO: fix stuttering with fade transition -->
              {#if degreeIsVisible}
                <h3 class="text-before-scroll" transition:fade>
                  Let us also look at rates of degree attainment in America.
                </h3>
              {/if}
            </div>
          </ObservedArticleText>
        </div>
      {/snippet}

      {#snippet scrolly()}
        <div>
          <a href="" target="_blank"
            ><img
              class="degreeRates"
              src="DegreeAttainment.png"
              alt="Graph that shows "
            /></a
          >
        </div>

        <ArticleText>
          <p>
            This graph from the BWDC shows that according to the National Center
            for Education Statistics (NCES), 43.3% of white people earned a
            bachelor's degree or higher between 2011-2023. That is 13.3% more
            than Black people and 20.8% more than Hispanic people. This
            difference can again be due to a variety of reasons, but we are
            focusing on the potential <em>impact</em> this difference may have on
            these minorities.
          </p>
        </ArticleText>
      {/snippet}
    </Scroller>

    <Scroller layout="right">
      {#snippet sticky()}
        <ObservedArticleText callback={setIncomeVisibility} {options}>
          <div class="start-section">
            <!-- TODO: fix stuttering with fade transition -->
            {#if incomeIsVisible}
              <h3 class="text-before-scroll" transition:fade>
                We know that generational wealth positively impacts the rate of
                high educational achievement. We will now look the relationship
                between education level and income. Examine the following
                graphs.
              </h3>
            {/if}
          </div>
        </ObservedArticleText>
      {/snippet}

      {#snippet scrolly()}
        <div>
          <a href="" target="_blank"
            ><img
              class="hsIncome"
              src="high-school-income.png"
              alt="Graph that shows "
            /></a
          >
        </div>

        <div>
          <a href="" target="_blank"
            ><img
              class="collegeIncome"
              src="college-income.png"
              alt="Graph that shows "
            /></a
          >
        </div>

        <ArticleText>
          <p>
            The first graph shows Median Annual Earnings for Full-Time Workers
            (25-34) by Race/Ethnicity among those who have only obtained a high
            school diploma while the second graph shows the same data but among
            those who have earned a bachelor's degree or higher. There is a
            marked increase in income among those who completed a bachelor's
            degree or higher, regardless of race or ethnicity.
          </p>
        </ArticleText>

        <ArticleText>
          <p>
            We have found evidence that a high education level corresponds to
            higher income. However, higher education also offers other benefits,
            such as the <a
              href="https://www.luminafoundation.org/files/resources/its-not-just-the-money.pdf"
              >opportunity to build important connections with other
              professionals ("social wealth" or "social capital")</a
            >.
          </p>
        </ArticleText>
      {/snippet}
    </Scroller>

    <div class="afterText">
      <ArticleText>
        <p>
          The benefits of higher education all seem to translate into more
          potential generational wealth to pass onto children. However, did you
          notice a trend that stood out in these graphs?
        </p>
      </ArticleText>

      <ArticleText>
        <p>
          One observation of the presented information could be that white
          people in this data had higher advanced education rates and higher
          income levels (regardless of education level) than Black and Hispanic
          people. Since generational wealth can lead to higher advanced
          education rates and a higher education level can lead to a higher
          income level, this racial wealth gap could be partially attributed to
          the higher amount of wealth that white people of older generations
          have (compared to Black/Hispanic people in the same age groups).

          <br />
          <br />
          We may have uncovered an impact of generational wealth on the current racial
          wealth gap.
        </p>
      </ArticleText>
    </div>
  </div>
</main>

<style>
  /* h4 {
    color: #f2e9e4;
    opacity: 80%;
    text-align: center;
    font-size: 28px;
    padding-bottom: 50px;
    font-family: "SpaceMono";
    font-style: italic;
  } */
  .wealthCollegeImage,
  .collegeIncome,
  .hsIncome,
  .degreeRates {
    margin: auto;
    width: 90%;
    box-shadow: 12px 12px 12px black;
    border: solid #4a4e69 4px;
    border-radius: 6px;
    text-align: center;
  }

  .tableauPlaceholder {
    margin-top: 20px;
    margin-bottom: 20px;
  }

  a {
    color: #9a8c98;
  }

  .afterText {
    background-color: #c9ada7;
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    align-items: flex-start;
    /* padding: 30px;
    padding-top: 200px;
    margin-top: 100px; */
    padding: min(20vh, 20rem) 1rem;
  }

  h3 {
    font-family: "Cinzel";
    font-style: italic;
    font-size: 28px;
    text-align: center;
    padding: 40px;
  }
</style>
