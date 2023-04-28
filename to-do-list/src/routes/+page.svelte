<svelte:head>
    <link rel="stylesheet" href="https://unpkg.com/@picocss/pico@latest/css/pico.min.css">
</svelte:head>

<div style="margin: 0 auto; padding: 20px; width: 700px">
    <h2 style="text-align: center">To-Do List</h2>
    <p>Enter your task here:</p>
    <div style="display: flex;">
        <input type="text">
        <button style="width: 150px;">Add</button>
    </div>
</div>

<div style="display: flex; align-items: baseline; width: 700px; margin: 0 auto;">
    <input type="checkbox">
    <h4 style="flex-grow: 1;">Will become list item</h4>
    <div style="display:flex;">
        <button>Edit</button>
        <button>Delete</button>
    </div>
</div>