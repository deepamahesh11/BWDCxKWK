<!-- TitleCard.svelte -->
<script>
  export let title;
  export let subtitle;
</script>

<div class="content-box">
  <h1>{title}</h1>
  <p>{subtitle}</p>
</div>

<style>
  .content-box {
    max-width: 700px;
    background-color: #947b8d;
    padding: 2rem;
    border-radius: 2rem;
    box-shadow: 16px 16px #58144a;
    text-align: center;
    font-family: "Lucida Console", "Courier New", monospace;
  }

  h1 {
    font-family: "Lucida Console", "Courier New", monospace;
    font-size: 3rem;
    margin: 0;
    color: #471238;
    text-shadow: 1px 1px 0 #007052;
  }

  p {
    font-size: 1.3rem;
    color: #471238;
    margin-top: 1rem;
  }

  @media (max-width: 600px) {
    h1 {
      font-size: 2.2rem;
    }
    p {
      font-size: 1.1rem;
    }
  }
</style>