<script>
	let toDoList = []; //To-Do List array
    let textInput = '';

    function addToDo() {
        toDoList = [...toDoList, { content: textInput, editing: false, checked: true }];
    }

	function setEditing(i, isEditing) {
		toDoList[i].editing = isEditing; // true/false
	}

    function deleteToDo(i) {
        toDoList.splice(i, 1);
        toDoList = toDoList; // svelte won't recognize the modified array until we update toDoList to it's modified version --> tells compiler to update the interface
    }
</script>

<svelte:head>
	<link rel="stylesheet" href="https://unpkg.com/@picocss/pico@latest/css/pico.min.css" />
</svelte:head>

<div style="margin: 0 auto; padding: 20px; width: 700px">
	<h2 style="text-align: center">To-Do List</h2>
	<p>Enter your task here:</p>
	<div style="display: flex;">
		<input type="text" bind:value={textInput}/>
		<button style="width: 150px;" on:click={addToDo}>Add</button>
	</div>
</div>

{#each toDoList as toDo, i}
	<div style="display: flex; align-items: baseline; width: 700px; margin: 0 auto;">
		{#if toDo.editing}
			<input type="text" bind:value={toDo.content} />
		{:else}
			<input type="checkbox" bind:checked={toDo.checked} />
			<h4 style="flex-grow: 1;">{toDo.content}</h4>
		{/if}
		<div style="display: flex;">
			{#if toDo.editing}
				<button on:click={() => setEditing(i, false)}>Save</button>
			{:else}
				<button on:click={() => setEditing(i, true)}>Edit</button>
			{/if}
			<button on:click={() => deleteToDo(i)}>Delete</button>
		</div>
	</div>
{/each}
