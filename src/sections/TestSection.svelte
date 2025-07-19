<script>
    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";







</script>




<div>
    <Scroller layout="left">
    {#snippet sticky()}
        
    {/snippet}

    {#snippet scrolly()}
        <ArticleText>

            hi my name is Deepa
            
        </ArticleText>
    {/snippet}
</Scroller>
</div>