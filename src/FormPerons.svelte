<script>
  let name;
  let beltColor;
  let age;
  let running = false;
  let swimming = false;
  let climbing = false;

  const handleSubmit = () => {
    console.log(name, age, beltColor);
  };
</script>

<style>
</style>

<form on:submit|preventDefault={handleSubmit}>
  <input class="formb" type="text" placeholder="name" bind:value={name} />
  <input
    class="formb"
    type="text"
    placeholder="belt color"
    bind:value={beltColor} />
  <input class="formb" type="norm" placeholder="age" bind:value={age} />
  <label>Skills:</label>
  <input type="checkbox" bind:checked={running} />Running<br />
  <input type="checkbox" bind:checked={swimming} />Swimming<br />
  <input type="checkbox" bind:checked={climbing} />Climbing<br />
  <button class="buttonb">Add person</button>
</form>
