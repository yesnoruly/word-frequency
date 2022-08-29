<script>
    export let words;
</script>

<table>
    <thead>
        <tr>
            <th colspan="1">Word</th>
            <th colspan="1">Frequency</th>
        </tr>
    </thead>

    <tbody>
        {#each words as {word, num}}
            <tr>
                <td colspan="1">{word}</td>
                <td colspan="1">{num}</td>
            </tr>
        {/each}
    </tbody>
</table>

<style>
    table {
        text-align: center;
    }
</style>