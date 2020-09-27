<script>

    function addRow() {
        data = [...data, [...newRow]]
        newRow = columns
    }

    function deletedRow(rowToBeDeleted) {
        data = data.filter(row => row != rowToBeDeleted)
    }

    let columns = ["Name", "Emails", "Phone Number"]

    let data = [
        ["John", "john@example.com", "081 7433 8121"],
        ["Matt", "matt@gmail.com", "081 43332 5091"],
        ["Mike", "mike@yahoo.com", "081 8150 1323"],
        ["Dave", "dave@btinternet.com", "081 1021 4007"]
    ]

    let newRow = [...columns];

</script>

<table>
    <tr>
        {#each columns as column}
            <th>{column}</th>
        {/each}
    </tr>

    {#each data as row}
        <tr>
            {#each row as cell}
                <td contenteditable="true" bind:innerHTML={cell} />
            {/each}
            <button on:click={() => deletedRow(row)}>X</button>
        </tr>
    {/each}

    <tr class="new">
        {#each newRow as column}
            <td contenteditable="true" bind:innerHTML={column} />
        {/each}
        <button on:click={addRow}>add</button>
    </tr>

</table>

<style>
    body{
        background-color: white;
    }
    .new{
        color:grey;
    }
    .new td:focus {
        color:black;
    }
</style>