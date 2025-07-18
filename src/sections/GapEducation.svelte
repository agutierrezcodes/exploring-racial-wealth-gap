<script>
  import SubsectionCard from "../lib/SubsectionCard.svelte";
  import * as Highcharts from "highcharts";
  import "highcharts/modules/exporting";
  import { Chart } from "@highcharts/svelte";
  import Scroller from "../lib/Scroller.svelte";
  import ObservedArticleText from "../lib/ObservedArticleText.svelte";
  import ArticleText from "../lib/ArticleText.svelte";

  const subheader = "THE IMPACT OF THE GAP";
  const subtitle = "Education";

  const options = {
    threshold: [0.88, 0.93],
  };
</script>

<main>
  <SubsectionCard {subheader} {subtitle} />

  <div class="genWealthSection">
    <Scroller layout="right">
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
              compared to their Black and Hispanic peers, potentially due to the
              generational wealth gap. It may be more feasible for white people
              from older generations to pass on wealth to their descendants than
              it is for Black and Hispanic people of the same generations.
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
