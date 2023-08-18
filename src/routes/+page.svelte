<script>
  let dd = 1;
  let mo = 1;
  let yr;
  const dt = new Date();

  let age = {
    years: 0,
    months: 0,
    days: 0
  }
  let maxyear = yr = (new Date()).getFullYear();
  $: {
    age.years = (dt.getFullYear() - yr) || 0; 
    age.months = (dt.getMonth() + 1) - mo || 0;
    if (age.months < 0) {
      age.years--;
      age.months += 12;
    }
    age.days = (dt.getDate() - dd) || 0; 
  }
</script>
<style>
  .attribution { font-size: 11px; text-align: center; }
  .attribution a { color: hsl(228, 45%, 44%); }
  .grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1rem;
    align-items: center;
    font-size: 1.2rem;
    margin-bottom: 1rem;
  }
  .app-title {
    font-size: 1.3vw;
    margin-bottom: 1rem;
    text-align: center;
  }
  .age-input {
    font-size: 1.2rem;
    border: none;
    box-shadow: 0 0 4px #999;
    padding: 0.5rem;
    width: 6rem;
  }
  main {
    box-sizing: border-box;
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    width: 30rem;
    margin: 1vh auto;
    padding: 2rem;
    border-radius: 1rem 1rem 8rem 1rem;
    box-shadow: 0 0 4px #999;
  }
  .age-box {
    display: flex;
    flex-direction: column;
    gap: 1rem;
    padding: 1rem;
    margin: 1rem auto 1rem;
    width: fit-content;
  }
  .age {
    font-family: helvetica;
    font-size: 2rem;
    font-style: italic;
    font-weight: 600;
    color: #333;
  }
  .age .clr {
    color: purple;
    font-weight: inherit;
  }
  .arrow {
    background: url(../assets/images/icon-arrow.svg) no-repeat 0 50%;
  }
  @media screen and (max-width: 480px) {
    .app-title {
      font-size: 5vw;
    }
  }
</style>

<main>
  <div class="app-title">Frontend Mentor | Age calculator app</div>

  <div class="grid">
    <div>Day</div>
    <div>Month</div>
    <div>Year</div>
  </div>
  <div class="grid">
    <div><label for="dd"><input id="dd" class="age-input" type="number" bind:value={dd} min={1} max={31}></label></div>
    <div><label for="mm"><input id="mm" class="age-input" type="number" bind:value={mo} min={1} max={12}></label></div>
    <div><label for="yy"><input id="yy" class="age-input" type="number" bind:value={yr} min={1900} max={maxyear}></label></div>
  </div>
  <div class="arrow">
    <hr>
  </div>
  <div class="age-box">
    <div class="age"><span class="clr">{age.years}</span> years</div>
    <div class="age"><span class="clr">{age.months}</span> months</div>
    <div class="age"><span class="clr">{age.days}</span> days</div>
  </div>

  <div class="attribution">
    Challenge by <a href="https://www.frontendmentor.io?ref=challenge" target="_blank">Frontend Mentor</a>. 
    Coded by <a href="https://github.com/srikantgudi/age-calculator" target="_app">Srikant Gudi</a>.
  </div>
</main>
