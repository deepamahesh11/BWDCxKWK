<script>
  import LeftAlignedExample from "./sections/LeftAlignedExample.svelte";
  import PopulationsStatesGeorgia from "./sections/PopulationsStatesGeorgia.svelte";
  import PopulationsStatesCalifornia from "./sections/PopulationsStatesCalifornia.svelte";
  import ImageExample from "./sections/ImageExample.svelte";
  import TitleSection from "./sections/TitleSection.svelte";
  import InteresectionObserverBasicExample from "./sections/InteresectionObserverBasicExample.svelte";
  import IntersectionObserverAlertExample from "./sections/IntersectionObserverAlertExample.svelte";
  import DisappearingDuckExample from "./sections/DisappearingDuckExample.svelte";
  import IntersectionObserverSectionCard from "./sections/IntersectionObserverSectionCard.svelte";
  import IntersectionObserverListExample from "./sections/IntersectionObserverListExample.svelte";
  import TestSection from "./sections/TestSection.svelte";
  import DeepaIntro from "./sections/DeepaIntro.svelte";
  import EndSection from "./sections/EndSection.svelte";
</script>

<main>
  <TitleSection />
  <div style= "height: 30vh; background-color: #370f28;"></div>
  <DeepaIntro />
  <div style= "height: 30vh; background-color: #370f28;"></div>
  <PopulationsStatesCalifornia />
  <PopulationsStatesGeorgia/>
  <!-- <LeftAlignedExample />
  <ImageExample />

  <IntersectionObserverSectionCard />
  <InteresectionObserverBasicExample />
  <IntersectionObserverAlertExample />
  <DisappearingDuckExample />
  <IntersectionObserverListExample /> -->

  <TestSection />
  <EndSection />
</main>
