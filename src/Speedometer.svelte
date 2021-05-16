<script>
  import Inputs from "./Inputs.svelte";
  import Calculator from "./Calculator.svelte";

  let inputValues = {
    distance: 1,
    speedOne: 1,
    speedTwo: 1,
  };
</script>

<Inputs bind:inputValues />
<Calculator {inputValues} />
