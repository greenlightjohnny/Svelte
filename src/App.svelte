<script>
  import { text } from "svelte/internal";
  import Modal from "./modal.svelte";

  import FormPerson from "./FormPerons.svelte";
  let showModal = false;
  // let lastName = "Hendrix";
  // let beltColor = "black";

  // $: fullName = `${firstName} ${lastName}`;
  // $: {
  //   console.log(beltColor);
  //   console.log(fullName);
  // }

  // const handleClick = () => {
  //   beltColor = "orange";
  // };

  // const handleInput = (e) => {
  //   beltColor = e.target.value;
  // };

  let people = [
    { name: "Kim", beltColor: "Black", age: 25, id: 1 },
    { name: "Jim", beltColor: "Blue", age: 21, id: 2 },
    { name: "Tim", beltColor: "Purple", age: 31, id: 3 },
  ];

  const handleClick = (id) => {
    people = people.filter((person) => person.id != id);
  };
  let num = 0;

  const toggleModal = () => {
    showModal = !showModal;
  };

  const addPersonEvent = (e) => {
    const person = e.detail;
    people = [person, ...people];
    showModal = false;
  };
</script>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }

  .formb {
    display: inline-block;
    max-width: 200px;
  }

  .buttonb {
    display: block;
    margin: 0 auto;
  }
</style>

{#if num > 20}
  <p>Greater than 20</p>
{:else if num > 5}
  <p>Greater than 5</p>
{:else}
  <!-- <p>Not greater than 5</p> -->
{/if}
<Modal {showModal} isPromo={false} on:click={toggleModal}>
  <!-- <h3>Add a new person</h3> -->
  <FormPerson on:addPerson={addPersonEvent} />
</Modal>
<main>
  <!-- <p>{fullName} - belt</p>
  <input type="text" bind:value={firstName} />
  <input type="text" bind:value={lastName} />
  <input type="text" bind:value={beltColor} /> -->
  <button on:click={toggleModal}>Modal</button>
  {#each people as person (person.id)}
    <div>
      <h4>{person.name}</h4>
      {#if person.beltColor === 'Black'}
        <p><strong>MASTER</strong></p>
      {/if}
      <p>{person.age} years old, {person.beltColor} belt.</p>
      <button on:click|once={() => handleClick(person.id)}>Delete</button>
    </div>
  {:else}
    <p>There are no people</p>
  {/each}
</main>
