<script>
  import { text } from "svelte/internal";

  export let firstName = "Sam";
  let lastName = "Hendrix";
  let beltColor = "black";

  $: fullName = `${firstName} ${lastName}`;
  $: {
    console.log(beltColor);
    console.log(fullName);
  }

  const handleClick = () => {
    beltColor = "orange";
  };

  const handleInput = (e) => {
    beltColor = e.target.value;
  };

  let people = [{ name: "Kim" }];
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
</style>

<main>
  <p>{fullName} - belt</p>
  <input type="text" bind:value={firstName} />
  <input type="text" bind:value={lastName} />
  <input type="text" bind:value={beltColor} />
</main>
