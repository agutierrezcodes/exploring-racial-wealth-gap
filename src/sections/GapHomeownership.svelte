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
    threshold: 0.01,
  };

  let homeIntroIsVisible = $state(true);
  let recapIsVisible = $state(true);
  let interestIsVisible = $state(true);

  const setInterestVisibility = (entries, observer) => {
    entries.forEach((entry) => {
      const elem = entry.target;

      if (entry.intersectionRatio >= 0.01) {
        interestIsVisible = true;
      } else if (entry.intersectionRatio < 0.01) {
        interestIsVisible = false;
      }
    });
  };

  const setHomeIntroVisibility = (entries, observer) => {
    entries.forEach((entry) => {
      const elem = entry.target;

      if (entry.intersectionRatio >= 0.01) {
        homeIntroIsVisible = true;
      } else if (entry.intersectionRatio < 0.01) {
        homeIntroIsVisible = false;
      }
    });
  };
</script>

<main>
  <SubsectionCard {subheader} {subtitle} />

  <div class="gapHomeSection">
    <div class="beforeEmbed">
      <div class="start-section">
        <ObservedArticleText callback={setHomeIntroVisibility} {options}>
          <!-- TODO: fix stuttering with fade transition -->
          {#if homeIntroIsVisible}
            <h3
              class="text-before-scroll"
              transition:fade={{ delay: 50, duration: 1000 }}
            >
              By this point, you might already see where this is going, but if
              not, no worries! We will briefly recap what we have seen so far!
            </h3>
          {/if}
        </ObservedArticleText>
      </div>

      <br />

      <!-- <ObservedArticleText callback={setRecapVisibility} {options}> -->
      <div class="recap">
        <!-- TODO: fix stuttering with fade transition -->

        <ArticleText>
          {#if recapIsVisible}
            <ol transition:fade={{ delay: 50, duration: 1000 }}>
              <li>
                The racial wealth gap in the United States has existed for
                generations. As of 2019, the median white household has more
                wealth than the median Black households and median Hispanic
                households.
              </li>
              <img
                class="arrow"
                src="down-arrow.png"
                alt="arrow pointing down"
              />
              <li>
                Wealth positively impacts a person's chances of obtaining a
                higher education (bachelor's degree or higher).
              </li>
              <img
                class="arrow"
                src="down-arrow.png"
                alt="arrow pointing down"
              />
              <li>A higher education correlates to a higher income level.</li>
            </ol>

            <br />

            <p>But how does this relate to homeownership rates?</p>
          {/if}
        </ArticleText>
      </div>
      <!-- </ObservedArticleText> -->

      <br />

      <Scroller layout="left">
        {#snippet sticky()}
          <div class="homeIntroSection">
            <h2 transition:fade={{ delay: 50, duration: 1000 }}>
              Homeownership Rates
            </h2>
          </div>
        {/snippet}

        {#snippet scrolly()}
          <!-- <ObservedArticleText callback={() => {}} {options}> -->
          <div>
            <ArticleText>
              <p>
                We previously found evidence that a higher education correlates
                to a higher income level. So, how exactly does a higher income
                level factor in when buying a home?
              </p>
            </ArticleText>

            <ArticleText>
              <p>
                This <a
                  href="https://www.ib.barclays/content/dam/barclaysmicrosites/ibpublic/documents/our-insights/HousingReform/barclays-impact-series-8-addressing-a-growing-divide.pdf"
                  target="_blank">report from Barclays</a
                > found that "The homeownership rate for households with low income
                (below $25,000) is 46%, a figure that may in fact be bolstered by
                the presence in this group of retirees and other people who have
                purchased homes when earning higher incomes. The rate is nearly two
                times higher for households at the top of the income distribution
                (above $132,000) at 84%."
              </p>
            </ArticleText>

            <ArticleText>
              <p>
                Another finding of this report is that between 1983 to 2019,
                White Americans consistently had higher rates of homeownership
                compared to Black Americans.
              </p>
            </ArticleText>

            <a
              href="https://www.ib.barclays/content/dam/barclaysmicrosites/ibpublic/documents/our-insights/HousingReform/barclays-impact-series-8-addressing-a-growing-divide.pdf "
              ><img
                src="homeownership-race.png"
                alt="Graph that shows Homeownership rate by Race, 1983-2019"
              /></a
            >
            <ArticleText>
              <p>
                But, let's be extra careful and check their claims against
                another reliable source.
              </p>
            </ArticleText>

            <ArticleText>
              <p>
                The following <a
                  href="https://www.census.gov/library/stories/2022/11/homeownership-by-young-households-below-pre-great-recession-levels.html"
                  target="_blank">graphs from the United States Census</a
                >
                shows that a higher percentage of young people with some form of
                higher education had a higher homeownership rate than those who had
                less than a high school education. Of those with a Bachelor's degree
                or higher, the race/ethnicity with the highest homeownership rate
                was also found to be Non-Hispanic White, supporting Barclay's findings.
              </p>
            </ArticleText>

            <a
              href="https://www.census.gov/library/stories/2022/11/homeownership-by-young-households-below-pre-great-recession-levels.html"
              ><img
                src="homeownership-education.png"
                alt="Graph that shows US Young Householder Homeownership Rates by Education: 2000-2019"
              /></a
            >

            <a
              href="https://www.census.gov/library/stories/2022/11/homeownership-by-young-households-below-pre-great-recession-levels.html"
              ><img
                src="homeownership.png"
                alt="Graph that shows US Homeownership Rates of Young Householders with Bachelor's Degrees or Higher by Race or Hispanic Origin: 2000-2019"
              /></a
            >

            <ArticleText>
              <p>
                The report from the United States Census acknowledged that
                <a
                  href="https://www.census.gov/library/stories/2022/11/homeownership-by-young-households-below-pre-great-recession-levels.html"
                  target="_blank"
                  >homeownership rates of people 25 to 34 years old have fallen
                  since their height between 2003-2007, due to factors including
                  the 2007-2009 Recession</a
                >, but concluded that the gap in homeownership rates between
                races persists.
              </p>
            </ArticleText>

            <ArticleText>
              <p>
                These findings support the idea that a higher income level leads
                to a higher likelihood of eventual homeownership, and reveals
                that white people are more likely to own a home than Black and
                Hispanic people.
              </p>
            </ArticleText>

            <ArticleText>
              <p>
                At this point, you might be asking, "Income level appears to
                play a part in this gap in homeownership rates between different
                races, but are there other factors that could explain it?" which
                is a fantastic question! Next, we will review other factors that
                might explain this difference.
              </p>
            </ArticleText>

            <ArticleText>
              <p>
                One of the first steps towards purchasing a home typically
                involves applying for a loan. Let us look at a breakdown of Loan
                Actions Taken and Loan Product Type by Race or Ethnicity.
              </p>
            </ArticleText>

            <a href="https://blackwealthdata.org/explore/homeownership"
              ><img
                src="loanActions.png"
                alt="Graph that shows Loan Actions Taken and Loan Product Type by Race or
                Ethnicity - Loan Originated"
              /></a
            >
            <ArticleText>
              <p>
                One potential takeaway from this graph of 2023 data might be
                that White and Asian people appear to originate more loans
                compared to Black and Hispanic people. Let's change the "Action
                Taken" field from "Loan Originated" to "Application Denied" to
                see what else we might find.
              </p>
            </ArticleText>

            <a href="https://blackwealthdata.org/explore/homeownership"
              ><img
                src="loanDenied.png"
                alt="Graph that shows Loan Actions Taken and Loan Product Type by Race or
                Ethnicity - Application Denied"
              /></a
            >

            <ArticleText>
              <p>
                Did the graph reveal what you expected? This data implies that
                while Black Americans originate fewer loans than White and Asian
                Americans, they experience the highest number of application
                denials for loans. This barrier could factor into the lower
                homeownership rate for Black Americans that we noticed earlier.
                But is this the only barrier that Black loan-seekers face when
                applying for a home loan?
              </p>
            </ArticleText>
          </div>
          <!-- </ObservedArticleText> -->
        {/snippet}
      </Scroller>

      <Scroller layout="right">
        {#snippet sticky()}
          <div class="interestSection">
            <ObservedArticleText callback={setInterestVisibility} {options}>
              <div class="homeIntroSection">
                <h2 transition:fade={{ delay: 50, duration: 1000 }}>
                  Interest Rates
                </h2>
              </div>
            </ObservedArticleText>
          </div>
        {/snippet}

        {#snippet scrolly()}
          <div>
            <a
              href="https://www.jchs.harvard.edu/blog/high-income-black-homeowners-receive-higher-interest-rates-low-income-white-homeowners"
              ><img
                src="interestRates.png"
                alt="Graph that shows Median Mortgage Interest Rate (Percent) - 2019"
              /></a
            >
            <ArticleText>
              <p>
                Data from the 2019 American Housing Survey found that Black
                homeowners consistently had higher interest rates than White
                homeowners, regardless of income level. This data might reveal
                another barrier that Black loan-seekers must overcome to own a
                home.
              </p>
            </ArticleText>
          </div>
        {/snippet}
      </Scroller>
    </div>

    <div>
      <div class="additional-notes">
        <h3>
          Unfortunately, there is a <a
            href="https://massbudget.org/2021/08/06/a-history-of-racist-federal-housing-policies/"
            target="_blank"
            >long history of racist policies in America (including red-lining,
            descrimination in loan approval processes, exclusion from the 1944
            GI Bill, etc.)</a
          > that have made it harder for Black and Hispanic Americans to purchase
          homes. These policies have contributed to the gap in homeownership rates
          that we see today.
        </h3>
      </div>

      <div class="additional-notes">
        <h3>
          The graph below from the BWDC shows the Homeownership Rate, by
          Race/Ethnicity, of individual United States counties.

          <br />
          <br />

          <span class="challenge">Challenge:</span>

          <br />
          <br />

          Use this graph to find the Homeownership Rate breakdown of one county
          of your choice!
        </h3>
      </div>
    </div>

    <div
      class="tableauPlaceholder"
      id="viz1753099445939"
      style="position: relative"
    >
      <noscript
        ><a href="https:&#47;&#47;blackwealthdata.org&#47;explore&#47;assets"
          ><img
            alt="Percent Owner Occupied Housing Units "
            src="https:&#47;&#47;public.tableau.com&#47;static&#47;images&#47;PM&#47;PMYYBNR8Y&#47;1_rss.png"
            style="border: none"
          /></a
        ></noscript
      ><object class="tableauViz" style="display:none;"
        ><param name="host_url" value="https%3A%2F%2Fpublic.tableau.com%2F" />
        <param name="embed_code_version" value="3" />
        <param name="path" value="shared&#47;PMYYBNR8Y" />
        <param name="toolbar" value="yes" /><param
          name="static_image"
          value="https:&#47;&#47;public.tableau.com&#47;static&#47;images&#47;PM&#47;PMYYBNR8Y&#47;1.png"
        /> <param name="animate_transition" value="yes" /><param
          name="display_static_image"
          value="yes"
        /><param name="display_spinner" value="yes" /><param
          name="display_overlay"
          value="yes"
        /><param name="display_count" value="yes" /><param
          name="language"
          value="en-US"
        /><param name="origin" value="viz_share_link" /><param
          name="filter"
          value="padding=0"
        /><param name="filter" value="position=relative" /></object
      >
    </div>
    <script type="text/javascript">
      var divElement = document.getElementById("viz1753099445939");
      var vizElement = divElement.getElementsByTagName("object")[0];
      vizElement.style.width = "1244px";
      vizElement.style.height = "727px";
      var scriptElement = document.createElement("script");
      scriptElement.src =
        "https://public.tableau.com/javascripts/api/viz_v1.js";
      vizElement.parentNode.insertBefore(scriptElement, vizElement);
    </script>
  </div>
</main>

<style>
  .gapHomeSection {
    margin-top: 50rem;
    margin-bottom: 50rem;

    box-shadow: 16px 16px 12px #22223b;
    background-color: #4a4e69;
  }

  .challenge {
    font-weight: 600;
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

  p,
  h3,
  ol,
  li {
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

  .arrow {
    display: block;
    margin-right: auto;
    margin-left: auto;
    text-align: center;
    height: 50px;
    max-width: 8%;
    opacity: 15%;
    padding-top: 2%;
    padding-bottom: 2%;
    border: none;
  }

  img {
    display: block;
    margin-right: auto;
    margin-left: auto;
    text-align: center;
    max-width: 80%;
    border: outset #9a8c98 8px;
  }

  .recap {
    text-align: center;
    padding: 1rem;
  }

  .tableauPlaceholder {
    margin: auto;
    width: 90%;
    box-shadow: 12px 12px 12px black;

    border-radius: 6px;
    text-align: center;

    max-width: 90%;
  }

  .tableauPlaceholder {
    margin-top: 20px;
    margin-bottom: 20px;
    border: outset #9a8c98 10px;

    background-color: #4a4e69;
  }

  .beforeEmbed {
    background-color: #c9ada7;

    padding-top: 3rem;
  }

  div.homeIntroSection h2,
  .challenge {
    font-family: "Cinzel";
    font-style: italic;
    font-size: 32px;
    text-align: center;
    color: #22223b;
  }

  .additional-notes {
    background-color: #c9ada7;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    /* padding: 30px;
    padding-top: 200px;
    margin-top: 100px; */
    padding: min(20vh, 20rem) 1rem;
  }
</style>
