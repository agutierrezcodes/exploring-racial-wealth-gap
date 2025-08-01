<script>
  import SubsectionCard from "../lib/SubsectionCard.svelte";
  import "highcharts/modules/exporting";
  import Scroller from "../lib/Scroller.svelte";
  import ObservedArticleText from "../lib/ObservedArticleText.svelte";
  import ArticleText from "../lib/ArticleText.svelte";
  import { fade } from "svelte/transition";

  const subheader = "THE IMPACT OF THE GAP";
  const subtitle = "The racial wealth gap and higher education";

  const options = {
    threshold: 0.01,
  };

  let edIntroIsVisible = $state(true);
  let degreeIsVisible = $state(true);
  let incomeIsVisible = $state(true);
  let outro1IsVisible = $state(true);
  let outro2IsVisible = $state(true);
  let outro3IsVisible = $state(true);

  const setoutro1Visibility = (entries, observer) => {
    entries.forEach((entry) => {
      const elem = entry.target;

      if (entry.intersectionRatio >= 0.01) {
        outro1IsVisible = true;
      } else if (entry.intersectionRatio < 0.01) {
        outro1IsVisible = false;
      }
    });
  };

  const setoutro2Visibility = (entries, observer) => {
    entries.forEach((entry) => {
      const elem = entry.target;

      if (entry.intersectionRatio >= 0.01) {
        outro2IsVisible = true;
      } else if (entry.intersectionRatio < 0.01) {
        outro2IsVisible = false;
      }
    });
  };

  const setoutro3Visibility = (entries, observer) => {
    entries.forEach((entry) => {
      const elem = entry.target;

      if (entry.intersectionRatio >= 0.01) {
        outro3IsVisible = true;
      } else if (entry.intersectionRatio < 0.01) {
        outro3IsVisible = false;
      }
    });
  };

  const setIncomeVisibility = (entries, observer) => {
    entries.forEach((entry) => {
      const elem = entry.target;

      if (entry.intersectionRatio >= 0.01) {
        incomeIsVisible = true;
      } else if (entry.intersectionRatio < 0.01) {
        incomeIsVisible = false;
      }
    });
  };

  const setDegreeVisibility = (entries, observer) => {
    entries.forEach((entry) => {
      const elem = entry.target;

      if (entry.intersectionRatio >= 0.01) {
        degreeIsVisible = true;
      } else if (entry.intersectionRatio < 0.01) {
        degreeIsVisible = false;
      }
    });
  };

  const setEdIntroVisibility = (entries, observer) => {
    entries.forEach((entry) => {
      const elem = entry.target;

      if (entry.intersectionRatio >= 0.01) {
        edIntroIsVisible = true;
      } else if (entry.intersectionRatio < 0.01) {
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
                <h3
                  class="text-before-scroll"
                  transition:fade={{ delay: 50, duration: 1000 }}
                >
                  Wealth does not only influence finances. There is
                  <a
                    href="https://www.ihep.org/wp-content/uploads/2024/05/IHEP_RWG_FINAL.pdf"
                    target="_blank"
                    >evidence of a positive relationship between wealth and high
                    educational achievement</a
                  > (attending college/achieving a bachelor's degree or higher).
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
                <h3
                  class="text-before-scroll"
                  transition:fade={{ delay: 50, duration: 1000 }}
                >
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
              <h3
                class="text-before-scroll"
                transition:fade={{ delay: 50, duration: 1000 }}
              >
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
          <h3 class="observation">IMPORTANT OBSERVATION</h3>
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
      <ObservedArticleText callback={setoutro1Visibility} {options}>
        <div class="start-section">
          <!-- TODO: fix stuttering with fade transition -->
          {#if outro1IsVisible}
            <h3
              class="text-after-scroll"
              transition:fade={{ delay: 50, duration: 1000 }}
            >
              The benefits of higher education all appear to translate into more
              potential generational wealth to pass on. However, did you notice
              a trend that stood out in these graphs?
            </h3>
          {/if}
        </div>
      </ObservedArticleText>
    </div>

    <div class="afterText">
      <ObservedArticleText callback={setoutro2Visibility} {options}>
        <div class="start-section">
          <!-- TODO: fix stuttering with fade transition -->
          {#if outro2IsVisible}
            <h3
              class="text-after-scroll"
              transition:fade={{ delay: 50, duration: 1000 }}
            >
              One observation of the presented information could be that white
              people in this data had higher advanced education rates and higher
              income levels (regardless of education level) than Black and
              Hispanic people. Since we have learned that generational wealth
              can lead to higher advanced education rates and a higher education
              level can lead to a higher income level, we might conclude that
              the racial wealth gap could be partially attributed to the higher
              amount of wealth that white people of older generations have
              (compared to Black/Hispanic people in the same age groups).

              <br />
              <br />
              We might have just uncovered two impacts of the racial wealth gap and
              learned how generational wealth has played a part in maintaining the
              gap.
            </h3>
          {/if}
        </div>
      </ObservedArticleText>
    </div>

    <div class="finalText">
      <ObservedArticleText callback={setoutro3Visibility} {options}>
        <div class="start-section">
          <!-- TODO: fix stuttering with fade transition -->
          {#if outro3IsVisible}
            <h3
              class="text-after-scroll"
              transition:fade={{ delay: 50, duration: 1000 }}
            >
              But, can we take this even further?
            </h3>
          {/if}
        </div>
      </ObservedArticleText>
    </div>
  </div>
</main>

<style>
  .gapEdSection {
    margin-top: 50rem;
    margin-bottom: 50rem;

    box-shadow: 16px 16px 12px #22223b;
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
    border: ridge #4a4e69;
    /* Code credit for advanced hemisphere border style: https://www.entheosweb.com/tutorials/css-borders-tutorial/ */
    border-width: 4px 14px 4px 14px;
    border-radius: 100px 100px 0 0;
    -moz-border-radius: 100px 100px 0 0;
    -webkit-border-radius: 100px 100px 0 0;
    margin: 8%;
    box-shadow: 12px 12px 16px black;
    color: #f2e9e4;
  }

  h3 > a {
    color: #4a4e69;
  }
  .observation {
    font-family: "Cinzel";
    font-style: italic;
    font-size: 28px;
    text-align: center;
    padding: 50px;
    border-style: ridge;
    border-color: #c9ada7;
    border-radius: 4px;
    border-width: 8px;
    background-color: #4a4e69;
    color: #f2e9e4;
    margin: 10%;

    box-shadow: 12px 12px 16px black;
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
</style>
