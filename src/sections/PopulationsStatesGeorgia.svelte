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
            backgroundColor: "#ADD8E6", 
            height: 400,
            width: 400
        },
        title: {
            text: "Georgia's Ethnicity Demographic",
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
      { name: "Latino", y: 10 },
      { name: "White", y: 50 },
      { name: "Asian American or Pacific Islander", y: 4.3 },
      { name: "Black", y: 31 },

    ]
  }
]
    };




    let options1 = {
        chart: {
            type: "pie",
            backgroundColor: "#ffd700", 
            height: 400,
            width: 400
        },
        title: {
            text: "Georgia's Business Demographic",
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
                        sliced: true,
                        selected: true,
                        y: 132275,
                    },
                    {
                        name: "Black",
                        sliced: true,
                        selected: true,
                        y: 14009,
                    },
                    {
                        name: "Hispanic",
                        y: 7067,
                    },
                    {
                        name: "Asian",
                        y: 25065
                    }

  
                ],
            },
        ],
    };








































</script>

<div style= "background-color: #370f28">
    <Scroller layout="right">
        {#snippet sticky()}
<div class="chart-row">
  <div class="chart-wrapper">
    <Chart {options} highcharts={Highcharts} />
    <div class="chart-text">
      <a href="https://datausa.io/profile/geo/georgia">source</a>
    </div>
  </div>

 {#if showSecondChart}
  <div class="chart-wrapper" transition:fade>
    <Chart options = {options1} highcharts={Highcharts} />
    <div class="chart-text">
      <a href="https://public.tableau.com/shared/7BZGFYM4K?:display_count=n&:origin=viz_share_link&:embed=y">BWDC source</a>
    </div>
  </div>
  {/if}
</div>
{/snippet}

        {#snippet scrolly()}
        
            <ArticleText>
                <div class="grid-container" style="color:#ADD8E6">
                 <img src="DeepaTalking.gif" alt="Deepa is talking" style="width: 100px; height: 100px;" />
                <strong>Let's take a look at the Number of Employer Firms in Georgia. But before doing so, let's look at the population spread. </strong
                >
                </div>
            </ArticleText>

            <ArticleText>
                <div class="grid-container" style="color:#ADD8E6">
                 <img src="DeepaTalking.gif" alt="Deepa is talking" style="width: 100px; height: 100px;" />
                <strong>Looking at Georgia's population, the most important thing here to notice is that the percentage of Black people is higher. 31 percent.</strong
                >
                </div>


            </ArticleText>
            <ArticleText>
                <div class="grid-container" style="color:#ADD8E6">
                 <img src="DeepaTalking.gif" alt="Deepa is talking" style="width: 100px; height: 100px;" />
                <strong>So you would think that because there are more black people, there would be more black owned businesses right?</strong
                >
                </div>


            </ArticleText>



            <div use:inview>
                <ArticleText>
                     
                   <div class="grid-container" style="color:#ffd700">
                    <img src="DeepaTalking.gif" alt="Deepa is talking" style="width: 100px; height: 100px;" />
                    <strong>WRONG.</strong>
                   </div>

                </ArticleText>
            </div>



    
        
            <ArticleText>
                <div class="grid-container" style="color:#ffd700">
                 <img src="DeepaTalking.gif" alt="Deepa is talking" style="width: 100px; height: 100px;" />
                <strong>There are over 132K White owned businesses in Georgia but only 14K Black owned businesses! </strong>
                </div>
            </ArticleText>

            <ArticleText>
                <div class="grid-container">
                 <img src="DeepaTalking.gif" alt="Deepa is talking" style="width: 100px; height: 100px;" />
                <strong>Why despite a more diverse percentage-wise population, there are still less Black owned businesses?</strong
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