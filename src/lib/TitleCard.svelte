<script>
  let { title, subtitle, scroll, scrollImg, scrollImgAlt } = $props();
</script>

<div class="title-card">
  <div class="content">
    <h1 class="title-text">{title}</h1>
    <p>{subtitle}</p>
  </div>
  <br />
  <div>
    <h4 class="scroll-text">{scroll}</h4>

    <img class="down-arrow" src={scrollImg} alt={scrollImgAlt} />
  </div>
</div>

<style>
  .title-card {
    background-color: #4a4e69;
    height: 100vh;
    display: block;
    justify-content: center;
    align-items: center;
    text-align: center;
  }

  .title-text {
    font-family: "Cinzel";
  }

  .content {
    max-width: 100%;
    background-color: #c9ada7;
    padding: 4rem;
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
    font-family: "Maitree";
    font-style: italic;

    font-weight: 300;
  }

  h4 {
    color: #f2e9e4;
    opacity: 20%;
    text-align: center;
    font-size: 24px;
    font-family: "Maitree" semibold;
    font-style: italic;
    font-weight: 500;
  }

  img {
    display: block;
    margin-right: auto;
    margin-left: auto;
    text-align: center;
    height: 50px;
    max-width: 8%;
    opacity: 15%;

    padding-bottom: 50px;
  }

  @media (max-width: 600px) {
    h1 {
      font-size: 2.2rem;
    }

    p {
      font-size: 1.1rem;
    }

    /* .down-arrow {
      position: absolute;
      top: calc(100vh - 80px);
      left: calc(50% - 14px);
      width: 0;
      height: 30px;
      border: 2px solid;
      border-radius: 2px;
      animation: jumpInfinite 1.5s infinite;
    }

    .down-arrow:after {
      content: " ";
      position: absolute;
      top: 12px;
      left: -10px;
      width: 16px;
      height: 16px;
      border-bottom: 4px solid;
      border-right: 4px solid;
      border-radius: 4px;
      transform: rotateZ(45deg);
    }

    @keyframes jumpInfinite {
      0% {
        margin-top: 0;
      }
      50% {
        margin-top: 20px;
      }
      100% {
        margin-top: 0;
      } 
    } */
  }
</style>
