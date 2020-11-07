<script>
  import { createEventDispatcher } from "svelte"
  let dispatch = createEventDispatcher()
  let name
  let beltColor
  let age

  let skills = []
  const handleSubmit = () => {
    const person = {
      name: name,
      beltColor: beltColor,
      age: age,
      skills: skills,
      id: Math.random(),
    }

    dispatch("addPerson", person)
  }
</script>

<style>
</style>

<form on:submit|preventDefault={handleSubmit}>
  <input class="formb" type="text" placeholder="name" bind:value={name} />
  <!-- <input
      class="formb"
      type="text"
      placeholder="belt color"
      bind:value={beltColor} /> -->
  <input class="formb" type="norm" placeholder="age" bind:value={age} />
  <label>Skills:</label>
  <!-- <input type="checkbox" bind:checked={running} />Running<br />
    <input type="checkbox" bind:checked={swimming} />Swimming<br />
    <input type="checkbox" bind:checked={climbing} />Climbing<br /> -->

  <input type="checkbox" bind:group={skills} value="running" />Running<br />
  <input type="checkbox" bind:group={skills} value="swimming" />Swimming<br />
  <input type="checkbox" bind:group={skills} value="climbing" />Climbing<br />
  <label>Belt Color</label>
  <select bind:value={beltColor}>
    <option value="black">black</option>
    <option value="brown">brown</option>
    <option value="purple">purple</option>
    <option value="blue">blue</option>
    <option value="white">white</option>
  </select>
  <button class="buttonb">Add person</button>
</form>
