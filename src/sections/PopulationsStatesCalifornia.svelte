<script>
    import * as Highcharts from "highcharts";
    import "highcharts/modules/exporting";
    import { Chart } from "@highcharts/svelte";
    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";
    import {fade, fly} from 'svelte/transition';


    let showSecondChart = $state(false);
    function inview(node) {
    const observer = new IntersectionObserver(
      ([entry]) => {
        if (entry.isIntersecting) {
          showSecondChart = true;
          observer.disconnect();
        }
      },
      { threshold: 0.5 }
    );

    observer.observe(node);

    return {
      destroy() {
        observer.disconnect();
      }
    };
  }


    let options = {
        chart: {
            type: "pie",
            backgroundColor: "#ffd700", 
            height: 400,
            width: 400

        },
        title: {
            text: "California's Business Demographic",
        

        },
        plotOptions: {
            pie: {
                allowPointSelect: true,
                dataLabels: [
                    {
                        enabled: true,
                        distance: 20,
                    },
                    {
                        enabled: true,
                        distance: -40,
                        format: "{point.percentage:.1f}%",
                        style: {
                            fontSize: "1.2em",
                            textOutline: "none",
                        },
                        filter: {
                            operator: ">",
                            property: "percentage",
                            value: 10,
                        },
                    },
                ],
            },
        },
        series: [
            {
                name: "Businesses",
                data: [
                    {
                        name: "White",
                        selected: true,
                        sliced:true,
                        y: 460730,
                    },
                    {
                        name: "Black",
                        sliced: true,
                        selected: true,
                        y: 13887,
                    },
                    {
                        name: "Hispanic",
                        y: 88290,
                    },
                    {
                        name: "Asian",
                        y: 168271
                    }

  
                ],
            },
        ],
    };


    let options1 = {
        chart: {
            type: "pie",
            backgroundColor: "#ADD8E6", 
            height: 400,
            width: 400
        },
        title: {
            text: "California's Ethnicity Demographic",
        },
        plotOptions: {
            pie: {
                allowPointSelect: true,
                dataLabels: [
                    {
                        enabled: true,
                        distance: 20,
                    },
                    {
                        enabled: true,
                        distance: -40,
                        format: "{point.name}: {point.y}%",
                        style: {
                            fontSize: "1.2em",
                            textOutline: "none",
                        },
                        filter: {
                            operator: ">",
                            property: "percentage",
                            value: 10,
                        },
                    },
                ],
            },
        },
series: [
  {
    name: "Population Percentage",
    data: [
      { name: "Latino", y: 40 },
      { name: "White", y: 34 },
      { name: "Asian American or Pacific Islander", y: 16 },
      { name: "Black", y: 6 },
      { name: "Multiracial", y: 3 },
      { name: "Native American or Alaska Native", y: 1 }
    ]
  }
]
    };








































</script>

<div style= "background-color: #370f28">
    <Scroller layout="right">
        {#snippet sticky()}
<div class="chart-row">
  <div class="chart-wrapper">
    <Chart {options} highcharts={Highcharts} />
    <div class="chart-text">
      <a href="https://public.tableau.com/shared/7BZGFYM4K?:display_count=n&:origin=viz_share_link&:embed=y">BWDC source</a>
    </div>
  </div>

 {#if showSecondChart}
  <div class="chart-wrapper" transition:fade>
    <Chart options = {options1} highcharts={Highcharts} />
    <div class="chart-text">
      <a href="https://www.ppic.org/publication/californias-population/">source</a>
    </div>
  </div>
  {/if}
</div>
{/snippet}

        {#snippet scrolly()}
        
            <ArticleText>
                <div class="grid-container" style="color:#ffd700">
                 <img src="DeepaTalking.gif" alt="Deepa is talking" style="width: 100px; height: 100px;" />
                <strong>Let's take a look at the Number of Employer Firms in the most populated state in the USA, California. Pretty crazy right?</strong
                >
                </div>
            </ArticleText>

            <ArticleText>
                <div class="grid-container" style="color:#ffd700">
                 <img src="DeepaTalking.gif" alt="Deepa is talking" style="width: 100px; height: 100px;" />
                <strong>About 63% of Employer Businesses are white owned whereas only about 2% of businesses are black-owned.
                    AKA:
                    There are over 460K White owned businesses but only over 14K Black owned businesses.</strong
                >
                </div>
            </ArticleText>

            <ArticleText>
                <div class="grid-container" style="color:#ffd700">
                 <img src="DeepaTalking.gif" alt="Deepa is talking" style="width: 100px; height: 100px;" />
                <strong>
                    But of course when looking at these numbers, we also must take into account the demographics of California. 

                </strong>

                </div>
            </ArticleText>




            <div use:inview>
                <ArticleText>
                   <div class="grid-container" style="color:#ADD8E6">
                    <img src="DeepaTalking.gif" alt="Deepa is talking" style="width: 100px; height: 100px;" />
                    <strong>We can see here that 34% of the population is White whereas 6% is black</strong>
                   </div>

                </ArticleText>
            </div>



    
        
            <ArticleText>
                <div class="grid-container" style="color:#ADD8E6">
                 <img src="DeepaTalking.gif" alt="Deepa is talking" style="width: 100px; height: 100px;" />
                <strong>So because there is such a difference in the population spread, would the difference
                     in the number of employer firms be less in a state that had a higher percentage of black people?</strong
                >
                </div>
            </ArticleText>

            <ArticleText>
                <div class="grid-container">
                 <img src="DeepaTalking.gif" alt="Deepa is talking" style="width: 100px; height: 100px;" />
                <strong>Let's find out. Keep scrolling.</strong
                >
                </div>
            </ArticleText>


        
        {/snippet}



        
    </Scroller>
</div>


<style>
.chart-row {
  display: flex;
  justify-content: center;
  gap: 10px; 
  flex-wrap: wrap;
}

.chart-wrapper {
  background-color: #947b8d;
  width: 420px;  
  padding: 0px;
  border-radius: 12px;
  box-sizing: border-box;
}

.chart-text {
  margin-top: 10px;
  color: white;
  font-size: 0.9rem;
  text-align: center;
}
  .grid-container {
  display: flex;
  align-items: center;
  gap: 15px;
  }

</style>