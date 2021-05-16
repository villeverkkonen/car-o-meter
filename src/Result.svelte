<script>
  export let car;
  export let consumptionOne = 0;
  export let consumptionTwo = 0;
  export let consumptionDifference = 0;

  function getCarPicture() {
    if (car === "A") {
      return `<img class="carPicture" src="images/carA.png" alt="Car A" />`;
    }
    if (car === "B") {
      return `<img class="carPicture" src="images/carB.png" alt="Car B" />`;
    }
    if (car === "C") {
      return `<img class="carPicture" src="images/carC.png" alt="Car C" />`;
    }
  }
</script>

<div class="result">
  {@html getCarPicture()}
  <p>
    <span class="openSans">Kulutus 1</span><span class="consumptionResult"
      >{consumptionOne.toFixed(3)}</span
    >
  </p>
  <p>
    <span class="openSans">Kulutus 2</span><span class="consumptionResult"
      >{consumptionTwo.toFixed(3)}</span
    >
  </p>
  <p>
    <span class="openSans">Erotus</span><span class="consumptionResult"
      >{consumptionDifference.toFixed(3)} litraa</span
    >
  </p>
</div>

<style>
  .consumptionResult {
    margin-left: 15px;
  }
</style>
