<script>
  import TitleCard from '../lib/TitleCard.svelte';
  import { fly } from 'svelte/transition';
  import { onDestroy, onMount, tick } from 'svelte';

  let showTitleCard = false;

  const title = "It is no secret that there are disparities between black owned and white owned businesses";
  const subtitle = "But how jarring is it?";

  function handleScroll() {
    const scrollY = window.scrollY;

    if (scrollY <= 10) {
        showTitleCard = true; 
    } else {
        showTitleCard = false;
    }



  }

  onMount(() => {
    handleScroll(); // Check position right away
    window.addEventListener('scroll', handleScroll);
  });

  onDestroy(() => {
    window.removeEventListener('scroll', handleScroll);
  });


</script>

<div class="background">
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
