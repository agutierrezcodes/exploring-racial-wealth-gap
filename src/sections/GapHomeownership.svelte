<script>
  import SubsectionCard from "../lib/SubsectionCard.svelte";
  import * as Highcharts from "highcharts";
  import "highcharts/modules/exporting";
  import { Chart } from "@highcharts/svelte";
  import Scroller from "../lib/Scroller.svelte";
  import ObservedArticleText from "../lib/ObservedArticleText.svelte";
  import ArticleText from "../lib/ArticleText.svelte";
  import { fade } from "svelte/transition";

  const subheader = "THE GAP HITS HOME";
  const subtitle = "The racial wealth gap and homeownership rates";

  const options = {
    threshold: [0.85, 0.95],
  };

  let homeIntroIsVisible = $state(true);
  let recapIsVisible = $state(true);
  let degreeIsVisible = $state(true);
  let incomeIsVisible = $state(true);

  const setRecapVisibility = (entries, observer) => {
    entries.forEach((entry) => {
      const elem = entry.target;

      if (entry.intersectionRatio >= 0.9) {
        recapIsVisible = true;
      } else if (entry.intersectionRatio < 0.9) {
        recapIsVisible = false;
      }
    });
  };

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

  const setHomeIntroVisibility = (entries, observer) => {
    entries.forEach((entry) => {
      const elem = entry.target;

      if (entry.intersectionRatio >= 0.9) {
        homeIntroIsVisible = true;
      } else if (entry.intersectionRatio < 0.9) {
        homeIntroIsVisible = false;
      }
    });
  };
</script>

<main>
  <SubsectionCard {subheader} {subtitle} />

  <div class="gapHomeSection">
    <ObservedArticleText callback={setHomeIntroVisibility} {options}>
      <div class="start-section">
        <!-- TODO: fix stuttering with fade transition -->
        {#if homeIntroIsVisible}
          <h3 class="text-before-scroll" transition:fade>
            By this point, you might already see where this is going, but if
            not, no worries! We will briefly recap what we have seen so far!
          </h3>
        {/if}
      </div>
    </ObservedArticleText>

    <ObservedArticleText callback={setRecapVisibility} {options}>
      <div class="start-section">
        <!-- TODO: fix stuttering with fade transition -->
        {#if recapIsVisible}
          <ArticleText>
            <ol>
              <li>The racial wealth gap in the United States has existed for generations. The median white household has more wealth than the median Black households and median Hispanic households. </li>
              <img src="down-arrow.png" alt="arrow pointing down" />
              <li>
                Wealth positively impacts a person's chances of obtaining a
                higher education (bachelor's degree or higher).
              </li>
              <img src="down-arrow.png" alt="arrow pointing down" />
              <li>A higher education correlates to a higher income level.</li>
            </ol>
          </ArticleText>
        {/if}
      </div>
    </ObservedArticleText>

    <Scroller layout="right">
      {#snippet sticky()}
        <div class="edIntroSection">
          <h1>Homeownership Rates</h1>
        </div>
      {/snippet}

      {#snippet scrolly()}
        <!-- <ObservedArticleText callback={() => {}} {options}> -->
        <div>
          <ArticleText>
            <p>
              The following graph summarizes part of <a
                href="https://www.urban.org/sites/default/files/publication/89976/wealth_and_education_3.pdf"
                target="_blank">Braga et al's</a
              > research, who found that “Young people from high-wealth families
              (wealth above roughly $223,500) are more than one and a half times
              as likely to complete at least two or four years of college by age
              25 as those in low-wealth families (wealth below $2,000).(1) High-wealth
              youth have a 70 percent chance of completing at least two years and
              a 43 percent chance of completing at least four years of college.”
            </p>
          </ArticleText>

          <div>
            <a
              href="https://www.urban.org/sites/default/files/publication/89976/wealth_and_education_3.pdf"
              target="_blank"
              ><img
                class="wealthCollegeImage"
                src="wealth-college.png"
                alt="Graph that shows percent of youth with at least 4 years of college attainment, broken down by income level"
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
                  Let us now look at rates of degree attainment in America.
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
              alt="Graph that shows Degree Attainment, by Race or Ethnicity"
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
                We will now consider the relationship between education level
                and income. Examine the following graphs.
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
              alt="Graph that shows Median Annual Earnings for Full-Time Workers
            (25-34 years old) by Race/Ethnicity (High school completion)"
            /></a
          >
        </div>

        <div>
          <a href="" target="_blank"
            ><img
              class="collegeIncome"
              src="college-income.png"
              alt="Graph that shows Median Annual Earnings for Full-Time Workers
            (25-34 years old) by Race/Ethnicity (Bachelor's or higher degree)"
            /></a
          >
        </div>

        <ArticleText>
          <p>
            The first graph shows Median Annual Earnings for Full-Time Workers
            (25-34 years old) by Race/Ethnicity among those who have only
            obtained a high school diploma while the second graph shows the same
            data but among those who have earned a bachelor's degree or higher.
            There is a marked increase in income among those who completed a
            bachelor's degree or higher, regardless of race or ethnicity.
          </p>
        </ArticleText>

        <ArticleText>
          <h3>IMPORTANT OBSERVATION</h3>
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

    <div class="afterText"></div>

    <div class="afterText"></div>

    <div class="finalText"></div>
  </div>
</main>

<style>
  .gapHomeSection {
    margin-top: 50rem;
    margin-bottom: 50rem;

    box-shadow: 16px 16px 12px #22223b;
    background-color: #c9ada7;
    padding-top: 3rem;
  }
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

  .afterText,
  .finalText {
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

  h3 {
    font-family: "Cinzel";
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

  .maiBold {
    font-weight: 600;
  }

  h3 > a {
    color: #4a4e69;
  }

  .text-before-scroll {
    font-family: "Maitree";
    font-style: normal;
    font-weight: 300;
    text-align: center;
  }

  p {
    font-family: "Maitree";
    font-style: normal;
    font-weight: 300;
  }

  div.afterText h3,
  div.finalText h3 {
    font-family: "Maitree";
    font-style: normal;
    font-weight: 300;
    font-size: 28px;
    text-align: center;
    padding: 50px;
    border-style: ridge;
    border-color: #4a4e69;
    border-radius: 4px;
    border-width: 8px;
    background-color: #9a8c98;
    color: #f2e9e4;
    margin: 10%;

    box-shadow: 12px 12px 16px black;
  }

  img {
    display: block;
    margin-right: auto;
    margin-left: auto;
    text-align: center;
    height: 50px;
    max-width: 8%;
    opacity: 15%;
    padding-top: 2%;
    padding-bottom: 2%;
  }
</style>
