<script>
  import TitleCard from '../lib/TitleCard.svelte';
  import { fly } from 'svelte/transition';
  import { onDestroy, onMount, tick } from 'svelte';

  let showTitleCard = true;

  const title = "Thank you for your time.";
  const subtitle = "This website was made by Deepa Mahesh for the KWKxBWDC Scrollytelling challenge. Thank you to Kode With Klossy and the Black Wealth Data Center for this opportunity.";

function inview(node) {
  const observer = new IntersectionObserver(([entry]) => {
    showTitleCard = entry.isIntersecting;
  }, {
    threshold: 0.5
  });

  observer.observe(node);

  return {
    destroy() {
      observer.disconnect();
    }
  };
}



</script>

<div class="background" use:inview>
  {#if showTitleCard}
    <div
      in:fly={{ y: 200, duration: 2000 }}
      out:fly={{ y: -200, duration: 2000 }}
    >
      <TitleCard {title} {subtitle} />
    </div>
  {/if}
</div>


<style>
  .background {
    background-color: #370f28;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    position: relative;
  }
</style>
