<script>
    import Table from "./lib/Table.svelte";
    import Diagram from "./lib/Diagram.svelte";
    import Input from "./lib/Input.svelte";

    let text = '';
    let words = [];

    function countWords() {
        if (text) {

            words = text
                .toLowerCase()
                .replace(/[^\w\s\\']|_/g, "") // Remove punctuations
                .replace(/[.,\/#!$%\^&\*;:{}=\-_`~()\s\t\r\n]/g, " ") // Replace empty lines, tabs, etc. with space
                .split(' ');

            let wordsFiltered = [...new Set(words)];

            // Generate array with objects
            words = wordsFiltered
                // Remove empty strings
                .filter(word => word !== '')
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

<Input bind:value={text} countWords={countWords} loadSample={loadSample} />

{#if words.length}
    <Table words={words}/>
    <Diagram />
{/if}
