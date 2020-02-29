
<script>
	let name = 'Anton';
	let age = 33;

	// let uppercaseName; dont required!

	$: uppercaseName = name.toUpperCase();

	function incrementAge (){
			age +=1;
	};
	function changeName (){
		name = 'AntonTarasenko';
	}
</script>

<style>
	h1 {
		color: purple;
	}
</style>

<h1>Hello {uppercaseName}, my age is {age}!</h1>
<button on:click="{incrementAge}">Change age</button>
<button on:click="{changeName}">Change Name</button>
