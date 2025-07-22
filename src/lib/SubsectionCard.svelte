<script>
  let { subheader, subtitle } = $props();
</script>

<div class="subheader-card">
  <div class="content">
    <h1 class="subheader-text">{subheader}</h1>
    <p>{subtitle}</p>
  </div>
</div>

<style>
  .subheader-card {
    background-color: #4a4e69;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
    padding: 2rem;
    box-sizing: border-box;
  }

  .subheader-text {
    font-family: "Cinzel";
  }

  .content {
    max-width: 800px;
    background-color: #c9ada7;
    padding: 8rem;
    border: 4px solid #f2e9e4;
    border-radius: 1.5rem;
    box-shadow: 16px 16px 12px #22223b;
  }

  h1 {
    font-size: 4rem;
    margin: 0;
    color: #22223b;
    text-shadow: 1px 1px 0 #22223b;
  }

  p {
    font-size: 1.6rem;
    color: #22223b;
    margin-top: 1rem;
    font-family: "Times New Roman";
    font-style: italic;
    font-weight: bold;
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
