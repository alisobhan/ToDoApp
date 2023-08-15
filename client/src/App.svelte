<script>
	 let name = "NotesApp";
	 let API_URL = "https://localhost:44363/"
	 let notes = "";
	 let newNotes = "";
	
	 function refreshList() {
		fetch(API_URL+"api/Notes/GetAll")
		.then(response => response.json())
		.then(data=> {
			notes=data;
		})
	 }

	 import { onMount } from "svelte";
	 onMount(async()=>{
		refreshList();
	 })
</script>

<main>
	<h2>{name}</h2>
	<input bind:value={newNotes}/>
	<button on:click={AddNote}></button>	
{#each notes as note}
	<p>
		<b>*{note.Description}</b>
	</p>
	{/each}
</main>

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