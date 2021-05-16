<script>
  export let inputValues = {
    distance: 1,
    speedOne: 1,
    speedTwo: 1,
  };
</script>

<div id="inputs">
  <div class="input">
    <label for="distanceInput" class="openSans">Matka</label>
    <input
      type="range"
      name="distance"
      id="distanceInput"
      bind:value={inputValues.distance}
      min="1"
      max="500"
    />
    <div class="inputValue">{inputValues.distance} km</div>
  </div>

  <div class="input">
    <label for="speedOneInput" class="openSans">Nopeus 1</label>
    <input
      type="range"
      name="speedOne"
      id="speedOneInput"
      bind:value={inputValues.speedOne}
      min="1"
      max="120"
    />
    <div class="inputValue">{inputValues.speedOne} km/h</div>
  </div>

  <div class="input">
    <label for="speedTwoInput" class="openSans">Nopeus 2</label>
    <input
      type="range"
      name="speedTwo"
      id="speedTwoInput"
      bind:value={inputValues.speedTwo}
      min="1"
      max="120"
    />
    <div class="inputValue">{inputValues.speedTwo} km/h</div>
  </div>
</div>

<style>
  #inputs {
    display: flex;
    justify-content: center;
  }

  .input {
    margin: 20px;
  }

  .inputValue {
    font-weight: bold;
  }

  @media only screen and (max-width: 560px) {
    #inputs {
      display: block;
    }
  }
</style>
