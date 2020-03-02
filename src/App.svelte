
<script>
	import ContactCard from "./ContactCard.svelte";

	let name = 'Anton';
	let title = '';
	let image ='';
	let description = '';
	let age = 33;

	// let uppercaseName; dont required!

	$: uppercaseName = name.toUpperCase();

	$: console.log(name);
	
	$: if (name === 'AntonTarasenko'){
		console.log('Its runs');
		age = 34;
	}

	function incrementAge (){
			age +=1;
	};
	function changeName (){
		name = 'AntonTarasenko';
	}

	function nameInput(event){
		const enteredValue = event.target.value;
		name = enteredValue;

	}
</script>

<style>
	h1 {
		color: purple;
	}
</style>

<h1>Hello {uppercaseName}, my age is {age}!</h1>
<button on:click="{incrementAge}">Change age</button>
<!-- <button on:click="{changeName}">Change Name</button> -->
<!-- <input type="text" value="{name}"on:input={nameInput}> -->
<input type="text" bind:value="{name}"/>
<input type="text" bind:value="{title}"/>
<input type="text" bind:value="{image}"/>
<textarea rows="3" bind:value="{description}"></textarea>

<ContactCard 
	userName="{name}"
	jobTitle="{title}"
	{description}
	userImage="{image}"
 />
