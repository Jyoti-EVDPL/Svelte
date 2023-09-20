<script>
	// Form Handling (Part 1)
	const formValues = {
		name:'',
		profileSummary:'',
		country:'',
		jobLocation:[],
	}

</script>

<main>
	<!-- Form Handling (Part 1) -->
	<div>
		<pre>
			{JSON.stringify(formValues,null,2)}
		</pre>
	</div>
	<form action="">
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
			<label for="country">Job </label>
			<select name="" id="country" bind:value={formValues.country}>
				<option value="">Select a country</option>
				<option value="india">india</option>
				<option value="china">china</option>
				<option value="brazil">brazil</option>
			</select>
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