<script>
  import { afterUpdate } from "svelte";
  import Result from "./Result.svelte";
  export let inputValues;
  let slope = 1.009;

  let consumptionA = 3;
  let consumptionB = 3.5;
  let consumptionC = 4;
  let consumptionOneForA = 0;
  let consumptionTwoForA = 0;
  let consumptionOneForB = 0;
  let consumptionTwoForB = 0;
  let consumptionOneForC = 0;
  let consumptionTwoForC = 0;
  let consumptionDifferenceForA = 0;
  let consumptionDifferenceForB = 0;
  let consumptionDifferenceForC = 0;

  let travelTimeOne = 0;
  let travelTimeTwo = 0;
  let travelTimeDifference = 0;

  afterUpdate(() => {
    consumptionOneForA = countTotalConsumption(
      inputValues.speedOne,
      inputValues.distance,
      consumptionA
    );
    consumptionTwoForA = countTotalConsumption(
      inputValues.speedTwo,
      inputValues.distance,
      consumptionA
    );

    consumptionOneForB = countTotalConsumption(
      inputValues.speedOne,
      inputValues.distance,
      consumptionB
    );
    consumptionTwoForB = countTotalConsumption(
      inputValues.speedTwo,
      inputValues.distance,
      consumptionB
    );

    consumptionOneForC = countTotalConsumption(
      inputValues.speedOne,
      inputValues.distance,
      consumptionC
    );
    consumptionTwoForC = countTotalConsumption(
      inputValues.speedTwo,
      inputValues.distance,
      consumptionC
    );

    travelTimeOne = countTravelTime(inputValues.distance, inputValues.speedOne);
    travelTimeTwo = countTravelTime(inputValues.distance, inputValues.speedTwo);
    countTimeDifference();
    countConsumptionDifferences();
  });

  function countTotalConsumption(speed, distance, consumption) {
    if (speed <= 1) {
      return (distance / 100) * speed * consumption;
    }

    for (let i = 1; i < speed; i++) {
      consumption = consumption * slope;
    }
    return (distance / 100) * consumption;
  }

  function countTravelTime(distance, speed) {
    return distance / speed;
  }

  function countTimeDifference() {
    if (travelTimeOne > travelTimeTwo) {
      travelTimeDifference = travelTimeOne - travelTimeTwo;
    } else {
      travelTimeDifference = travelTimeTwo - travelTimeOne;
    }
  }

  function countConsumptionDifferences() {
    if (consumptionOneForA > consumptionTwoForA) {
      consumptionDifferenceForA = consumptionOneForA - consumptionTwoForA;
    } else {
      consumptionDifferenceForA = consumptionTwoForA - consumptionOneForA;
    }

    if (consumptionOneForB > consumptionTwoForB) {
      consumptionDifferenceForB = consumptionOneForB - consumptionTwoForB;
    } else {
      consumptionDifferenceForB = consumptionTwoForB - consumptionOneForB;
    }

    if (consumptionOneForC > consumptionTwoForC) {
      consumptionDifferenceForC = consumptionOneForC - consumptionTwoForC;
    } else {
      consumptionDifferenceForC = consumptionTwoForC - consumptionOneForC;
    }
  }

  function timeConvert(num) {
    const seconds = num * 60 * 60;
    return new Date(seconds * 1000).toISOString().substr(11, 8);
  }
</script>

<div class="results consumptions">
  <Result
    car="A"
    consumptionOne={consumptionOneForA}
    consumptionTwo={consumptionTwoForA}
    consumptionDifference={consumptionDifferenceForA}
  />

  <Result
    car="B"
    consumptionOne={consumptionOneForB}
    consumptionTwo={consumptionTwoForB}
    consumptionDifference={consumptionDifferenceForB}
  />

  <Result
    car="C"
    consumptionOne={consumptionOneForC}
    consumptionTwo={consumptionTwoForC}
    consumptionDifference={consumptionDifferenceForC}
  />
</div>

<div class="results">
  <div class="result">
    <span class="openSans">Kesto 1</span>
    <br />
    <span>{timeConvert(travelTimeOne)}</span>
  </div>
  <div class="result">
    <span class="openSans">Kesto 2</span>
    <br />
    <span>{timeConvert(travelTimeTwo)}</span>
  </div>
</div>
<div class="result">
  <span class="openSans">Erotus</span>
  <br />
  <span>{timeConvert(travelTimeDifference)}</span>
</div>

<style>
  .results {
    display: flex;
    justify-content: center;
    align-items: flex-end;
  }

  @media only screen and (max-width: 560px) {
    .results {
      display: block;
    }
  }
</style>
