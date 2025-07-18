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

  <div class="gapEdSection">
    <Scroller layout="right">
      {#snippet sticky()}
        <ArticleText>
          <h3>
            Generational wealth does not just influence finances. There is a
            documented positive relationship between wealth and high educational
            achievement (attending college/achieving a bachelor's degree or
            higher).
          </h3>
        </ArticleText>
      {/snippet}

      {#snippet scrolly()}
        <!-- <ObservedArticleText callback={() => {}} {options}> -->
        <div>
          <ArticleText>
            <h3>
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
            </h3>
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

          <ArticleText>
            <h3>Let us also look at rates of degree attainment in America.</h3>
          </ArticleText>

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
            <h3>
              43.3% of white people earned a bachelor's degree or higher between
              2011-2023. That is 13.3% more than Black people and 20.8% more
              than Hispanic people. This difference can again be due to a
              variety of reasons, but we are focusing on the <em>impact</em> this
              difference may have on minorities.
            </h3>
          </ArticleText>

          <ArticleText>
            <h3>
              A higher level of eduation correlates to a higher income. Let us
              look at the following two graphs.
            </h3>
          </ArticleText>

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
            <h3>
              The first graph shows Median Income among those who have only
              completed high school while the second graph shows Median Income
              among those who have a bachelor's degree or higher. There is a
              marked increase in income among those who completed a bachelor's
              degree or higher in all races/ethnicities.
            </h3>
          </ArticleText>

          <ArticleText>
            <h3>
              Education not only correlates to higher income, but it also offers
              other benefits, such as the opportunity to build important
              connections with other professionals (also known as "social
              wealth").
            </h3>
          </ArticleText>

          <ArticleText>
            <h3>
              The benefits of higher education all translate into more wealth
              that can be transformed into generational wealth to pass onto
              children. However, did you notice something that stood out in
              these data sets? White people in this data had higher advanced
              education rates and income levels (regardless of education level)
              than Black and Hispanic people. We may have uncovered an impact of
              the generational wealth gap.
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
</style>
