<script>
    import { fade, fly } from "svelte/transition";
    import Scroller from "../lib/Scroller.svelte";
    import ObservedArticleText from "../lib/ObservedArticleText.svelte";

    let MapIsVisible = $state(false);

    const options = {
        threshold: [0.85, 0.95],
        
    };

    const MapSimpleCallback = (entries, observer) => {
        entries.forEach((entry) => {
            const elem = entry.target;

            if (entry.intersectionRatio >= 0.9) {
                // "active" state
                elem.style.backgroundColor = "#947b8d";
            } else if (entry.intersectionRatio < 0.9) {
                // "inactive" state
                elem.style.backgroundColor = "#888888";
            }
        });
    };

    const ShowMapCallback = (entries, observer) => {
        entries.forEach((entry) => {
            const elem = entry.target;

            if (entry.intersectionRatio >= 0.9) {
                elem.style.backgroundColor = "#947b8d";
                MapIsVisible = true;
            } else if (entry.intersectionRatio < 0.9) {
                elem.style.backgroundColor = "#888888";
            }
        });
    };

    const RemoveMapCallback = (entries, observer) => {
        entries.forEach((entry) => {
            const elem = entry.target;

            if (entry.intersectionRatio >= 0.9) {
                elem.style.backgroundColor = "#947b8d";
                MapIsVisible = false;
            } else if (entry.intersectionRatio < 0.9) {
                elem.style.backgroundColor = "#888888";
            }
        });
    };
</script>

<div>
    <Scroller layout="left">
        {#snippet sticky()}
            <div>
                {#if MapIsVisible}
                    <img
                        class="MapImage"
                        src="BWDCAtlanta.png"
                        alt="BWDC's Map of Banks in Atlanta"
                        in:fly={{ y: 200, duration: 2000 }}
                        out:fade
                    />
                {/if}
                <br />
            </div>
        {/snippet}

        {#snippet scrolly()}
        
            <ObservedArticleText callback={RemoveMapCallback} {options}>
                <div class="grid-container" style="color:black">
                 <img src="DeepaTalking.gif" alt="Deepa is talking" style="width: 100px; height: 100px;" />
                <strong>A reason for this we can find in data is the spread of banks in Georgia. Let's look specifically at Atlanta. </strong
                >
                <a href= "https://blackwealthdata.org/wealth-explorer/atlanta">Map from the BWDC of Atlanta</a>

                </div>
           

            </ObservedArticleText>

            <ObservedArticleText callback={ShowMapCallback} {options}>
                <div class="grid-container" style="color:black">
                 <img src="DeepaTalking.gif" alt="Deepa is talking" style="width: 100px; height: 100px;" />
                <strong>The dots in red are FDIC banks or Federal Deposit Insurance Corporation banks. Notice how they are all aligned in areas where there are less Black Owned businesses. 
                    This is no coincidence. The FDIC has a long history of not being accessible to black and minority owned business owners.  </strong
                >
                <a href="https://www.brookings.edu/articles/an-analysis-of-financial-institutions-in-black-majority-communities-black-borrowers-and-depositors-face-considerable-challenges-in-accessing-banking-services/">source</a>

                </div>
           

            </ObservedArticleText>

            <ObservedArticleText callback={MapSimpleCallback} {options}>
                <div class="grid-container" style="color:black">
                 <img src="DeepaTalking.gif" alt="Deepa is talking" style="width: 100px; height: 100px;" />
                <strong>The dots in purple are MDIs or Minority Depository Institutions. It has been said that they were created so Minorities could access mainstream financial resources.
                    You will notice that in areas closer to their locations, there is a higher amount of Black owned businesses.
                </strong>

                </div>
           

            </ObservedArticleText>

            <ObservedArticleText callback={MapSimpleCallback} {options}>
                <div class="grid-container" style="color:black">
                 <img src="DeepaTalking.gif" alt="Deepa is talking" style="width: 100px; height: 100px;" />
                <strong>The reason for this spread is not recent. This is an effect of "redlining", what the Home Owners' Loan Cooperation did in the 1930s to "highlight" more economically profitable areas.
                </strong>

                </div>
           

            </ObservedArticleText>
            <ObservedArticleText callback={MapSimpleCallback} {options}>
                <div class="grid-container" style="color:black">
                 <img src="DeepaTalking.gif" alt="Deepa is talking" style="width: 100px; height: 100px;" />
                <strong> This "redlining" process is nothing more of an effect of 1930s racism as areas with more minorities were labeled "Hazardous".
                    You can read more about this phenomenon and its effect today on Black people's access to banks in Atlanta in the source. </strong>

                    <a href= "https://ncrc.org/holc/">source on redlining</a>

                </div>
           

            </ObservedArticleText>

            <ObservedArticleText callback={MapSimpleCallback} {options}>
                <div class="grid-container" style="color:black">
                 <img src="DeepaTalking.gif" alt="Deepa is talking" style="width: 100px; height: 100px;" />
                <strong> It is the systemic racism embedded in the banking system that affects Black business owners from getting access to the financial resources they need to thrive. This is a major contribution as to why, even in 2025, the spread of White VS Black Business Owners isn't more even.  </strong>



                </div>
           

            </ObservedArticleText>

        {/snippet}
    </Scroller>
</div>

<style>
    .MapImage {
        width: 700px;
        height:500px
    }
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
