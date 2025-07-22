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
    <div class="beforeEmbed">
      <Scroller layout="left">
        {#snippet sticky()}
          <div class="homeIntroSection">
            <h2 transition:fade={{ delay: 50, duration: 1000 }}>
              What can we learn from this?
            </h2>
          </div>
        {/snippet}

        {#snippet scrolly()}
          <!-- <ObservedArticleText callback={() => {}} {options}> -->
          <div>
            <ArticleText>
              <p>
                To recap: the generational wealth gap contributes to the gap in
                educational attainment which in turn inhibits the likelihood of
                homeownership and the possibility of transferring ownership to
                descendants. (REMEMBER: homeownership is one of the primary ways
                in which generational wealth is built). And so, the cycle
                continues.
              </p>
              <p>
                Do we want to try to change this or continue the cycle? (option
                to cycle back to generational wealth at top of page or continue
                to solutions section)
              </p>
            </ArticleText>
          </div>
          <!-- </ObservedArticleText> -->
        {/snippet}
      </Scroller>

      <Scroller layout="right">
        {#snippet sticky()}
          <div class="degreeAttainSection">
            <ObservedArticleText callback={setDegreeVisibility} {options}>
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

    <ArticleText>
      <p>
        Unfortunately, there is a <a
          href="https://massbudget.org/2021/08/06/a-history-of-racist-federal-housing-policies/"
          target="_blank"
          >long history of racist policies (including red-lining, descrimination
          in loan approval processes, exclusion from the 1944 GI Bill)</a
        > in America that have made it harder for Black and Hispanic Americans to
        purchase homes. These policies have contributed to the gap in homeownership
        rates that we see today.
      </p>
    </ArticleText>

    <ArticleText>
      <p>
        The graph below from the BWDC shows the Homeownership Rate, by
        Race/Ethnicity, of individual United States counties.
      </p>

      <h4 class="challenge">Challenge:</h4>

      <p>
        Use this graph to find the Homeownership Rate breakdown of one county of
        your choice!
      </p>
    </ArticleText>

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
    background-color: #c9ada7;
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
  }

  img {
    display: block;
    margin-right: auto;
    margin-left: auto;
    text-align: center;
    max-width: 80%;
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
  }
</style>
