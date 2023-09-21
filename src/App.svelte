<script>
	// Form Handling (Part 1)
	const formValues = {
		name:'',
		profileSummary:'',
		country:'',
		jobLocation:[],
	}
	// Form Handling (Part 2)
	const formValues2 = {
		remoteWork:false,
		skillSet:[],
		yearsOfExp:'',
	}
	function submitForm(event){
		event.preventDefault(); //Or we can do this ny event modifier by using pipe(below function)
		console.log(formValues);
	}
	function submitForm2(){
		console.log(formValues2);
	}

</script>

<main>
	<!-- Form Handling (Part 1) -->
	<div>
		<pre>
			{JSON.stringify(formValues,null,2)}
		</pre>
	</div>
	<form on:submit={submitForm}>
		<div>
			<label for="Name">Name</label>
			<input type="text" id="name" bind:value={formValues.name}/>
		</div>
		<div>
			<label for="Profile">Profile Summary</label>
			<textarea name="" id="profile" cols="30" rows="10" bind:value={formValues.profileSummary}/>
		</div>
		<div>
			<label for="country">Country</label>
			<select name="" id="country" bind:value={formValues.country}>
				<option value="">Select a country</option>
				<option value="india">india</option>
				<option value="china">china</option>
				<option value="brazil">brazil</option>
			</select>
		</div>
		<div>
			<label for="job-location">Job Location</label>
			<select name="" id="job-location" bind:value={formValues.jobLocation} multiple>
				<option value="">Select a country</option>
				<option value="india">india</option>
				<option value="china">china</option>
				<option value="brazil">brazil</option>
			</select>
		</div>
		<div>
			<button>Submit</button>
		</div>
	</form>
<hr>
	<!-- Form Handling (Part 2) -->
	<div>
		<pre>
			{JSON.stringify(formValues2,null,2)}
		</pre>
	</div>
	<form on:submit|preventDefault={submitForm2}>
		<div>
			<!-- <input type/> -->
			<input type="checkbox" id="remoteWork" bind:checked={formValues2.remoteWork}>
			<label for="remoteWork">Open To Remote Work?</label>

		</div>
		<div>
			<!-- svelte-ignore a11y-label-has-associated-control -->
			<label>Skill Set</label>
			<input type="checkbox" id="html" value="html" bind:group={formValues2.skillSet}>
			<label for="skillSet">Html</label>
			<input type="checkbox" id="css" value="css" bind:group={formValues2.skillSet}>
			<label for="skillSet">Css</label>
			<input type="checkbox" id="js" value="js" bind:group={formValues2.skillSet}>
			<label for="skillSet">JS</label>
		</div>

		<div>
			<label>Years OF Experiance</label>
			<input type="radio" id="0-2" value="0-2" bind:group={formValues2.yearsOfExp}>
			<label for="0-2">0-2</label>
			<input type="radio" id="3-5" value="3-5" bind:group={formValues2.yearsOfExp}>
			<label for="3-5">3-5</label>
			<input type="radio" id="6-10" value="6-10" bind:group={formValues2.yearsOfExp}>
			<label for="6-10">6-10</label>
			<input type="radio" id="10+" value="10+" bind:group={formValues2.yearsOfExp}>
			<label for="10+">10+</label>
		</div>
		<div>
			<button>Submit2</button>
		</div>

	</form>


</main>

<style>
	input + label{
		display: inline-flex;
	}
	main {
		/* text-align: center; */
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