<script context="module">
	export async function load({ params }) {
		const { id } = params;
		const url = `https://pokeapi.co/api/v2/pokemon/${id}`;
		const res = await fetch(url);
		const pokeman = await res.json();

		return { props: { pokeman } };
	}
</script>

<script>
	export let pokeman;
</script>

<svelte:head>
  <link rel="icon" type="image/x-icon" href="pavicon.png">
</svelte:head>

<div class="flex flex-col items-center">

  <h1 class="text-4xl text-center my-8 uppercase">{pokeman.name}</h1>
  <p>
    Type: <strong>{pokeman.types[0].type.name}</strong> | Height:
    <strong>{pokeman.height} | Weight: <strong>{pokeman.weight}</strong></strong>
  </p>
  <img src={pokeman.sprites['front_default']} alt={pokeman.name} />
  
</div>