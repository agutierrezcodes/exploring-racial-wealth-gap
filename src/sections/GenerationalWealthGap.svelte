<script>
  import SubsectionCard from "../lib/SubsectionCard.svelte";
  import * as Highcharts from "highcharts";
  import "highcharts/modules/exporting";
  import { Chart } from "@highcharts/svelte";
  import Scroller from "../lib/Scroller.svelte";
  import ObservedArticleText from "../lib/ObservedArticleText.svelte";
  import ArticleText from "../lib/ArticleText.svelte";

  const subheader = "THE GENERATIONAL WEALTH GAP";
  const subtitle = "How big can it really be?";

  const options = {
    threshold: [0.88, 0.93],
  };
</script>

<main>
  <SubsectionCard {subheader} {subtitle} />

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
            <h3>
              While this graph is intended to display the Median Family Wealth,
              by Race or Ethnicity, between 1963 and 2019, if we look closer, we
              can <em>see</em> the difference in wealth that white Americans
              consistently appear to have, compared to Black and Hispanic
              Americans, going back roughly 3 generations (<a
                href="https://www.pewresearch.org/short-reads/2019/01/17/where-millennials-end-and-generation-z-begins/"
                >Generation X, Millenials, and Gen Z</a
              >).
            </h3>
          </ArticleText>

          <ArticleText>
            <h3>
              The median family wealth of all 3 racial/ethnic groups shown in
              this graph is generally increasing, lending to the idea that
              wealth is compounded through generations.
            </h3>
          </ArticleText>

          <div>
            <a href="https://blackwealthdata.org/explore/assets" target="_blank"
              ><img
                class="giftsImage"
                src="gifts.png"
                alt="Graph that shows Percent of 18-28 year olds who received gift or inheritance by Race/Ethnicity"
              /></a
            >
          </div>

          <ArticleText>
            <h3>
              The graph shown above shows that 2021 data revealed that a higher
              percent of white 18-28 year olds received gifts or an inheritance
              compared to their Black and Hispanic peers, potentially due to
              the generational wealth gap. It may be more feasible for white
              people from older generations to pass on wealth to their
              descendants than it is for Black and Hispanic people of the same
              generations.
            </h3>
          </ArticleText>

          <ArticleText>
            <h3>
              The table below, created by the Black Wealth Data Center (BWDC),
              breaks down the Percent of Households Holding Asset and Debt Types
              by Race/Ethnicity between 2007 and 2022. This data may also
              support the existence of the wealth gap between racial groups,
              especially when looking at the percent of white households with
              Directly Held Stocks and Pooled Investment Funds, compared to the
              percent of Black and Hispanic households who hold those same
              assets. While the percentages have increased since 2007, the gap
              remains.

              <br />
              <br />

              Take a look and see what else you might notice.
            </h3>
          </ArticleText>
        </div>
        <!-- </ObservedArticleText> -->
      {/snippet}
    </Scroller>

    <div
      class="tableauPlaceholder"
      id="viz1752825986571"
      style="position: relative"
    >
      <noscript
        ><a href="https:&#47;&#47;blackwealthdata.org&#47;explore&#47;assets"
          ><img
            alt="ADT08 "
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

    <Scroller layout="left">
      {#snippet sticky()}
        <!-- <ArticleText>
          <h3>
            You may ask "what is the significance of this wealth gap that has
            persisted for generations? How does this truly affect real people?".
          </h3>
        </ArticleText> -->
      {/snippet}

      {#snippet scrolly()}
        <ArticleText>
          <h3>
            The existence of this wealth gap between racial/ethnic groups in
            America has been <a
              href="https://apps.urban.org/features/wealth-inequality-charts/"
              >recognized and generational wealth is shown to contribute to it
            </a>, but it can be helpful to have it visualized to truly grasp it.
            While there are a variety of possible factors that could contribute
            this issue, we will solely consider the potential <em>impact</em> that
            this gap has had on Americans.
          </h3>
        </ArticleText>
      {/snippet}
    </Scroller>
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
  .wealthImage,
  .giftsImage,
  .tableauPlaceholder {
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
</style>
