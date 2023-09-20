<script>
	import { shuffle } from 'lodash';	
	export let name;
	const number = 0;
	const Click =()=>{
		// number = number+ 1;
		alert("Click");
	}
	const channel = '<b>New channel</b>';
	const hack = `<a href="#" onclick="alert('You have beeen hacked')">Win a prize</a>`;
	const Heading = 'heading';
	const disabled = false;
	// Class attribute:
	const status = 'success';
	const isPromoted = true;
	// Conditional Rendering:
	const num = 5 // num=5;'sdv'
	// List Renderings:
	const names = ['aanda','banda','senda'];
	const names2 = [
		{name:'aanda',age:5},
		{name:'karlo',age:4},
		{name:'marko',age:7}
	];
	// Lists and Keys
	let LK = ['aanda','banda','senda'];
	const ShuffleNames = ()=>{
		LK = shuffle(names);
	}


	// Form Handling (Part 1)

</script>

<main>
	<h1>Hello ChingChao {name}!</h1>
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>
	<button onclick={Click}>Click {number} Times</button>
	<div>{@html channel}</div>
	<div>{@html hack}</div>
	<h2 id={Heading}>This is h2 tag</h2>
	<h2 {Heading}>This is 2nd h2 tag</h2>
	<button {disabled}>Click Me</button>
	<!-- Class attribute: -->
	<h2 class={status}>Status</h2>
	<h2 class={isPromoted ? 'promoted' :''}>Movie Title</h2>
	<h2 class:promoted={isPromoted}>Movie Title2</h2>
	{#if num === 0}
	<h2>The num is 0</h2>
	{:else if num < 0}
	<h2>THe number is -ve</h2>
	{:else if num > 0}
	<h2>THe number is +ve</h2>
	{:else}
	<h2>Not a number</h2>
	{/if}
	
	<!-- List Renderings: -->
	{#each names as name}
	<h2>{name}</h2>
	{/each}

	{#each names as name,index}
	<h2>{index+1}:{name}</h2>
	{/each}

	{#each names2 as data,index}
	<h2>{index+1}.Name:{data.name}, Age:{data.age}</h2>
	{/each}
	<!-- Lists and Keys(helps to identify which item changed,add,remove or update) -->
	{#each LK as data (data)}
	<h3>{data}</h3>
	<input type="text" placeholder="Input Name">
	{/each}
	<div>
		<button on:click={ShuffleNames}>Shuffle</button>
	</div>

	<!-- Form Handling (Part 1) -->
	

</main>

<style>
	.danger{
		color: #ff3e00;
	}
	.success{
		color: chartreuse;
	}
	.promoted{
		font-style: italic;
	}


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