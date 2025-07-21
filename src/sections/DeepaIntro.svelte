<script>
  import ObservedArticleText from '../lib/ObservedArticleText.svelte';
  import { fade,fly } from 'svelte/transition';

  const bubbles = [
    "It is extremely jarring.",
    "Hi, my name is Deepa. Let's look at some numbers",
    "...keep scrolling you'll get there"
  ];

  let visibleIndex = 0;

  function handleIntersection(index) {
    return (entries) => {
      if (entries[0].isIntersecting) {
        visibleIndex = index;
      }
    };
  }

  const options = {
    threshold: 0.2
  };
</script>

<section style="position: relative; height: 600vh; background-color: #370f28; color: white;">

  <div
    style="
      position: sticky;
      top: 50%;
      transform: translateY(-50%);
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      height: 100vh;
      pointer-events: none;
      z-index: 10;
    "
  >
    <img src="DeepaTalking.gif" alt="Deepa is talking" style="width: 200px; height: 200px;" />
    <p
      style="
        background: rgba(255, 255, 255, 0.15);
        padding: 1rem;
        border-radius: 12px;
        text-align: center;
        margin-top: 2rem;
        max-width: 400px;
      "
      transition:fade
    >
      {bubbles[visibleIndex]}
    </p>
  </div>


<div class="observer-hidden">
  <ObservedArticleText callback={handleIntersection(0)} options={options}>
    First bubble text
  </ObservedArticleText>

  <div style="height: 100vh;"></div>

  <ObservedArticleText callback={handleIntersection(1)} options={options}>
    Second bubble text
  </ObservedArticleText>

  <div style="height: 100vh;"></div>

  <ObservedArticleText callback={handleIntersection(2)} options={options}>
    Third bubble text
  </ObservedArticleText>
</div>
</section>

<style>
  /* Scoped hiding of pink boxes only inside observer-hidden container */
 :global(.observer-hidden) :global(.article-text) {
    background: transparent !important;
    border: none !important;
    box-shadow: none !important;
    color: transparent !important;
    margin: 10vh auto !important; 
    padding: 0 !important;
    pointer-events: none;
  }
</style>


  