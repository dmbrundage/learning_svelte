<script>
    import {createEventDispatcher} from 'svelte';

    let dispatch = createEventDispatcher();

    let name;
    let beltColor;
    let age = 5;
    let Fighting;
    let Sneaking;
    let Diplomacy = true;
    let skills= []

    const handleSubmit = () => {
        const person = {name, beltColor, age, skills, id:Math.random() }

        dispatch('addPerson', person)
        
    }
</script>
<!-- forms have submission events and this can invoke a function when a button is pressed -->
<form on:submit|preventDefault={handleSubmit}>
    <input type="text" placeholder="first name" bind:value={name}>
    <input type="number" placeholder="age" bind:value={age}>
    <label>Skills:</label>
    <!-- this is one way of add checks but can be a lot -->
    <!-- <input type="checkbox" bind:checked={Fighting}>Fighting<br>
    <input type="checkbox" bind:checked={Sneaking}>Sneaking<br>
    <input type="checkbox" bind:checked={Diplomacy}>Diplomacy<br> -->

    <!-- the other way is binding to group property -->
    <!-- This uses the bind group to an empty erray and will append the value to the array on the action -->
    <input type="checkbox" bind:group={skills} value = "Fighting">Fighting<br>
    <input type="checkbox" bind:group={skills} value = "Sneaking">Sneaking<br>
    <input type="checkbox" bind:group={skills} value = "Diplomacy">Diplomacy<br>
    <label>Belt Color:</label>
    <select bind:value={beltColor}>
        <option value="Black">Black</option>
        <option value="Brown">Brown</option>
        <option value="Purple">Purple</option>
        <option value="Blue">Blue</option>
        <option value="White">White</option>
    </select>
    <div></div>
    <button>Add Person</button>
</form>

<style>

</style>