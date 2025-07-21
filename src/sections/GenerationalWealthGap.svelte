<script>
  import SubsectionCard from "../lib/SubsectionCard.svelte";
  import * as Highcharts from "highcharts";
  import "highcharts/modules/exporting";
  import { Chart } from "@highcharts/svelte";
  import Scroller from "../lib/Scroller.svelte";
  import ObservedArticleText from "../lib/ObservedArticleText.svelte";
  import ArticleText from "../lib/ArticleText.svelte";
  import { fade } from "svelte/transition";

  const subheader = "THE RACIAL WEALTH GAP";
  const subtitle = "How big can it really be?";

  let tableIntroIsVisible = $state(true);

  let tableOutroIsVisible = $state(true);

  const setTableIntroVisibility = (entries, observer) => {
    entries.forEach((entry) => {
      const elem = entry.target;

      if (entry.intersectionRatio >= 0.9) {
        tableIntroIsVisible = true;
      } else if (entry.intersectionRatio < 0.9) {
        tableIntroIsVisible = false;
      }
    });
  };

  const setTableOutroVisibility = (entries, observer) => {
    entries.forEach((entry) => {
      const elem = entry.target;

      if (entry.intersectionRatio >= 0.9) {
        tableOutroIsVisible = true;
      } else if (entry.intersectionRatio < 0.9) {
        tableOutroIsVisible = false;
      }
    });
  };

  const options = {
    threshold: [0.8, 1],
  };
</script>

<main>
  <SubsectionCard {subheader} {subtitle} />

  <div class="genWealthContent">
    <div class="genWealthSection">
      <Scroller layout="left">
        {#snippet sticky()}
          <div>
            <a
              href="https://www.urban.org/sites/default/files/publication/103267/closing-the-gaps-building-black-wealth-through-homeownership_1.pdf"
              target="_blank"
              ><img
                class="wealthImage"
                src="MedFamilyWealth.png"
                alt="Graph that shows Median Family Wealth, by Race/Ethnicity, 1963-2019"
              /></a
            >
          </div>
        {/snippet}

        {#snippet scrolly()}
          <!-- <ObservedArticleText callback={() => {}} {options}> -->
          <div>
            <ArticleText>
              <p>
                While this graph is intended to display the Median Family
                Wealth, by Race or Ethnicity, between 1963 and 2019, if we look
                closer, we can <em>see</em> the difference in wealth that white
                Americans consistently appear to have, compared to Black and
                Hispanic Americans, going back roughly 3 generations (<a
                  href="https://www.pewresearch.org/short-reads/2019/01/17/where-millennials-end-and-generation-z-begins/"
                  target="_blank">Generation X, Millenials, and Gen Z</a
                >). This graph might illustrate the racial wealth gap in the US,
                and it appears to span multiple generations.
              </p>
            </ArticleText>

            <ArticleText>
              <p>
                The median family wealth of all 3 racial/ethnic groups shown in
                this graph is generally increasing, also lending to the idea of
                wealth accumulating through generations.
              </p>
            </ArticleText>

            <div>
              <a
                href="https://blackwealthdata.org/explore/assets"
                target="_blank"
                ><img
                  class="giftsImage"
                  src="gifts.png"
                  alt="Graph that shows Percent of 18-28 year olds who received gift or inheritance by Race/Ethnicity"
                /></a
              >
            </div>

            <ArticleText>
              <p>
                The graph included above shows that data from a 2021 study
                revealed 16% percent of white 18-28 year olds received gifts or
                an inheritance, while 7.2% of their Black peers and 6.7% of
                their Hispanic peers received the same. Additionally, if you
                choose to explore this <a
                  href="https://public.tableau.com/views/BWDC-AssetsDebt-ADT13_17387909018670/ADT13?:language=en-US&padding=0&:embed=y&:sid=&:redirect=auth&:origin=viz_share_link&publish=yes&:display_count=n&position=relative"
                  target="_blank"
                  >graph from the Black Wealth Data Center (BWDC)</a
                > further, you will see that this study showed more white 18-28 year
                olds also received help paying expenses/bills, rent, and tuition.
              </p>
            </ArticleText>

            <ArticleText>
              <h3>IMPORTANT OBSERVATION</h3>
              <p>
                This difference in financial assistance could potentially due to
                the racial wealth gap. It may be more feasible for white people
                from older generations to pass on wealth to their descendants
                than it is for Black and Hispanic people of the same
                generations. The racial wealth gap between an older generation
                could influence the racial wealth gap between a younger
                generation.
              </p>
            </ArticleText>
          </div>
          <!-- </ObservedArticleText> -->
        {/snippet}
      </Scroller>

      <div class="beforeText">
        <ObservedArticleText callback={setTableIntroVisibility} {options}>
          <div class="start-section">
            <!-- TODO: fix stuttering with fade transition -->
            {#if tableIntroIsVisible}
              <h3 class="text-before-scroll" transition:fade>
                The table below, created by the Black Wealth Data Center (BWDC),
                breaks down the Percent of Households Holding Asset and Debt
                Types by Race/Ethnicity between 2007 and 2022. This data may
                also support the existence of the wealth gap between racial
                groups, especially when looking at the percent of white
                households with Directly Held Stocks and Pooled Investment
                Funds, compared to the percent of Black and Hispanic households
                who hold those same assets. While the percentages have increased
                since 2007, the gap remains.

                <br />
                <br />

                Take a look and see what else you might notice.
              </h3>
            {/if}
          </div>
        </ObservedArticleText>
      </div>

      <div
        class="tableauPlaceholder"
        id="viz1752825986571"
        style="position: relative"
      >
        <noscript
          ><a href="https:&#47;&#47;blackwealthdata.org&#47;explore&#47;assets"
            ><img
              alt="Interactive graph that shows Percent of Households Holding Asset & Debt Types, by Race/Ethnicity"
              src="https:&#47;&#47;public.tableau.com&#47;static&#47;images&#47;BW&#47;BWDC-AssetsDebt-PercentofHouseholdsHoldingAssetDebtTypes&#47;ADT08&#47;1_rss.png"
              style="border: none"
            /></a
          ></noscript
        ><object class="tableauViz" style="display:none;"
          ><param name="host_url" value="https%3A%2F%2Fpublic.tableau.com%2F" />
          <param name="embed_code_version" value="3" />
          <param name="site_root" value="" /><param
            name="name"
            value="BWDC-AssetsDebt-PercentofHouseholdsHoldingAssetDebtTypes&#47;ADT08"
          /><param name="tabs" value="no" /><param
            name="toolbar"
            value="yes"
          /><param
            name="static_image"
            value="https:&#47;&#47;public.tableau.com&#47;static&#47;images&#47;BW&#47;BWDC-AssetsDebt-PercentofHouseholdsHoldingAssetDebtTypes&#47;ADT08&#47;1.png"
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
        var divElement = document.getElementById("viz1752825986571");
        var vizElement = divElement.getElementsByTagName("object")[0];
        vizElement.style.width = "1244px";
        vizElement.style.height = "777px";
        var scriptElement = document.createElement("script");
        scriptElement.src =
          "https://public.tableau.com/javascripts/api/viz_v1.js";
        vizElement.parentNode.insertBefore(scriptElement, vizElement);
      </script>

      <!-- <Scroller layout="left">
      {#snippet sticky()}
        <ArticleText>
          <h3>
            You may ask "what is the significance of this wealth gap that has
            persisted for generations? How does this truly affect real people?".
          </h3>
        </ArticleText>
      {/snippet}

      {#snippet scrolly()}{/snippet}
    </Scroller> -->

      <div class="afterText">
        <ObservedArticleText callback={setTableOutroVisibility} {options}>
          <div class="start-section">
            <!-- TODO: fix stuttering with fade transition -->
            {#if tableOutroIsVisible}
              <h3 class="text-after-scroll" transition:fade>
                The existence of this wealth gap between racial/ethnic groups in
                America has been <a
                  href="https://apps.urban.org/features/wealth-inequality-charts/"
                  >recognized and there is evidence that generational wealth
                  contributes to it
                </a>, but it can be helpful to have it visualized to truly grasp
                it. While there are a variety of possible factors that could
                exacerbate this issue, we will solely consider the potential
                <em>impact</em> that this gap has had on Americans.
              </h3>
            {/if}
          </div>
        </ObservedArticleText>
      </div>

      <!-- <div class="afterText">
      <ArticleText>
        <p>
          The existence of this wealth gap between racial/ethnic groups in
          America has been <a
            href="https://apps.urban.org/features/wealth-inequality-charts/"
            >recognized and generational wealth is shown to contribute to it
          </a>, but it can be helpful to have it visualized to truly grasp it.
          While there are a variety of possible factors that could contribute
          this issue, we will solely consider the potential <em>impact</em> that
          this gap has had on Americans.
        </p>
      </ArticleText>
    </div> -->
    </div>
  </div>
</main>

<style>
  .genWealthSection {
    margin-top: 50rem;
    margin-bottom: 50rem;

    box-shadow: 16px 16px 12px #22223b;
  }

  h3 {
    font-family: "Cinzel";
    font-style: italic;
    font-size: 32px;
    text-align: center;
  }

  h3 {
    font-family: "Cinzel";
    font-style: italic;
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
  .wealthImage,
  .giftsImage,
  .tableauPlaceholder {
    margin: auto;
    width: 90%;
    box-shadow: 12px 12px 12px black;

    border-radius: 6px;
    text-align: center;
  }

  .tableauPlaceholder {
    margin-top: 20px;
    margin-bottom: 20px;
    border: outset #9a8c98 10px;
    max-width: 90%;
  }

  a {
    color: #9a8c98;
  }

  .beforeText,
  .afterText {
    height: 100vh;
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

  .text-before-scroll,
  .text-after-scroll {
    font-family: "Maitree";
    font-style: normal;
    font-weight: 300;
  }

  h3 > a {
    color: #4a4e69;
  }

  p {
    font-family: "Maitree";
    font-style: normal;
    font-weight: 300;
  }
</style>
