<script>
  import ContactCard from "./ContactCard.svelte";

  let name = "Empty";
  let title = "";
  let image = "";
  let description = "";
  // let done = false;
  let formState = 'empty';

  let createdContacts=[];

  function addContact (){
	  if(
		  name.trim().length == 0 ||
		  title.trim().length == 0 ||
		  image.trim().length ==0 ||
		  description.trim().length == 0
	  ){
		formState = 'invalid';
		return;
    }
    createdContacts = [
      ...createdContacts,
     {
       id: Math.random(),
      name: name, 
      jobTitle: title, 
      imageUrl: image, 
      desc: description
      }];
	  formState = 'done'
  }
  function deleteFirst (){
    createdContacts = createdContacts.slice(1);
  };
  function deleteLast (){
    createdContacts = createdContacts.slice(0, -1)
  };
</script>

<style>
  #form {
    width: 30rem;
    max-width: 100%;
  }
  .danger {
	  color: red
  }
</style>

<div id="form">
  <div class="form-control">
    <label for="userName">User Name</label>
    <input type="text" bind:value={name} id="userName" />
  </div>
  <div class="form-control">
    <label for="jobTitle">Job Title</label>
    <input type="text" bind:value={title} id="jobTitle" />
  </div>
  <div class="form-control">
    <label for="image">Image URL</label>
    <input type="text" bind:value={image} id="image" />
  </div>
  <div class="form-control">
    <label for="desc">Description</label>
    <textarea rows="3" bind:value={description} id="desc" />
  </div>
</div>
<button on:click="{addContact}">Add Contact Card</button>
<button on:click="{deleteFirst}">Delete First</button>
<button on:click="{deleteLast}">Delete Last</button>

 {#if formState === 'invalid'}
 <p class="danger">Change or choise your add's data</p>
 {:else}
 <p>Please entered some date add/or new prof data!</p>
 {/if}

{#each createdContacts as contact, i (contact.id)}
<h2># {i+1}</h2>
<ContactCard 
	userName={contact.name}
 	jobTitle={contact.jobTitle}
  description={contact.desc}
  userImage={contact.imageUrl}
 />
 {:else}
 <p>Please added one or more contacts</p>
{/each}