<script>
    import Table from "./lib/Table.svelte";
    import Diagram from "./lib/Diagram.svelte";

    let text = '';
    let words = [];

    function countWords() {
        if (text) {

            words = text
                .toLowerCase()
                .replace(/[^\w\s\\']|_/g, "") // Remove punctuations
                .replace(/\s+/g, " ") // Replace empty lines, tabs, etc. with space
                .split(' ');

            let wordsFiltered = [...new Set(words)];

            // Generate array with objects
            words = wordsFiltered
                .map((word) => {
                    // Get the number of the same words
                    let num = words.filter(x => x === word).length;
                    return {word, num};
                })
                .sort((firstWord, secondWord) => secondWord.num - firstWord.num);
            }
    }

    function loadSample() {
        text = '"Anything that happens, happens. Anything that, in happening, causes something else to happen, causes something else to happen. Anything that, in happening, causes itself to happen again, happens again. It doesn\'t necessarily do it in chronological order, though."'
    }
</script>

<div class="wf">
    <textarea bind:value={text} placeholder="Enter text"></textarea>
    <button class="btn-filled" on:click={countWords}>Count words</button>
    <button class="btn-empty" on:click={loadSample}>Load sample</button>
</div>

{#if words.length}
    <Table words={words}/>
    <Diagram />
{/if}



<style>
    .wf {
        background-color: #fff;
        padding: 35px 25px 25px;
        grid-area: wf;
    }

    textarea {

        font-family: 'Roboto Mono', sans-serif;
        width: 100%;
        min-height: 249px;
        resize: none;
        padding: 15px;

        background: #FFFFFF;
        border: 2px solid rgba(13, 107, 196, 0.6);
        border-radius: 2px;
        font-size: 14px;
        line-height: 21px;
        color: #023E96;
    }

    button {
        margin: 25px 25px 0 0;

        height: 40px;
        min-width: 130px;
        border-radius: 10px;
        text-align: center;
    }

    button:last-child {
        margin: 25px 0 0;
    }

    .btn-filled {
        background: #258CF4;
        color: #fff;
        border: none;
    }

    .btn-empty {
        background: #FFFFFF;
        border: 3px solid #258CF4;
        border-radius: 10px;
        color: #258CF4;
    }
</style>
