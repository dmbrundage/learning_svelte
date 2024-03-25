<script>
	//import components from component tree import __ from __
	import Modal from './Modal.svelte';
	import AddPersonForm from './AddPersonForm.svelte/'
	let showModal = false;
	let people = [
		{name: 'david', beltColor: 'black', age: 25, skills:[], id: 1},
		{name: 'sara', beltColor: 'orange', age: 25, skills:[], id: 2},
		{name: 'ziggy', beltColor: 'brown', age: 25, skills:[], id: 3}
		];
	
	const handleClick = (id) => {
		// filter people out of array by id passed from handler function
		people = people.filter((person) => person.id != id);
	}

	const updateModal = () => {
		console.log(showModal)
		// filter people out of array by id passed from handler function
		showModal = !showModal;
	}
	let num = 3;

	const addPerson = (e) => {
		const person = e.detail;
		people = [person, ...people]
		showModal = !showModal
	}

</script>

<!-- add component and pass props, prop name must match when used in child component -->
<!-- there is a shorthand when the prop and variable are the same you dont have to add prop name -->
<!-- If you dont self close the component you can pass child components or html as 'slots' -->
<!-- slots give options to pass content into components -->
<Modal isPromo = {true} {showModal} on:click={updateModal}>
<AddPersonForm on:addPerson={addPerson}/>
</Modal>
<main>
	<button on:click={updateModal}>Open Modal</button>
	<!-- this is the for loop syntax #each iterative_object as loop_variable (in parens binds loop variable to iterative) -->
	{#each people as person (person.id)}
	<div>
		<h4>{person.name}</h4>
		<!-- this is another example of conditional in svelte -->
		{#if person.beltColor === "black"}
			<p> <strong>Master Ninja</strong> </p>
		{/if}
		<p>{person.age} years old, {person.beltColor} belt color</p>
		{#each person.skills as skill}
		<p>{skill} </p>
		{/each}
		<!-- onclick in line function example so it wont run until clicked not on render -->
		<button on:click={() => handleClick(person.id)}>Delete</button>
	</div>
	{:else}
	<p>There are no people to show..</p>
	
	{/each}
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>