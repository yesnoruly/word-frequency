<script>
    export let words;
</script>

<div>
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
</div>

<style>
    div {
        grid-area: table;
        padding: 25px;

        background: #fff;
        position: relative;
    }

    div:before {
        content: '';
        background: url('../assets/icons/list.svg') no-repeat;
        width: 68px;
        height: 68px;
        position: absolute;
        left: -20px;
        top: -20px;
        transform: rotate(-25deg);
    }

    table {
        text-align: center;
        border-collapse: collapse;

        width: 100%;
        height: 100%;
    }

    thead {
        background: #258CF4;
        border-bottom: 3px solid #0D6BC4;
    }

    th {
        font-family: Roboto, sans-serif;
        font-size: 18px;
        text-transform: uppercase;
        color: #FFFFFF;
        padding: 10px;
        letter-spacing: 3px;

        width: 150px;
    }
    
    @media (max-width: 800px) {
        th {
            font-size: 14px;
        }
    }

    tr {
        font-family: Roboto, sans-serif;
        font-size: 14px;
        color: #000;
        line-height: 34px;
        letter-spacing: 1px;
        max-width: 150px;
        word-break: break-word;
    }

    tr:nth-child(odd) {
        background: rgba(37, 140, 244, 0.7);
    }
    tr:nth-child(even) {
        background: rgba(37, 140, 244, 0.2);
    }
</style>