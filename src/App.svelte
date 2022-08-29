<script>
    import Table from "./lib/Table.svelte";

    let text = '';
    let words = [];

    function loadSample() {
        text = '"Anything that happens, happens. Anything that, in happening, causes something else to happen, causes something else to happen. Anything that, in happening, causes itself to happen again, happens again. It doesn\'t necessarily do it in chronological order, though."'
    }

    function countWords() {
        if (text) {

            words = text
                .toLowerCase()
                .replace(/[^\w\s\\']|_/g, "") // Remove punctuations
                .replace(/\s+/g, " ") // Replace empty lines, tabs, etc. with space
                .split(' ');

            // Filter repeating words in array
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
</script>

<div class="wf">
    <textarea bind:value={text} id="textarea-freq" placeholder="Enter text"></textarea>
    <button on:click={countWords}>Count words</button>
    <button on:click={loadSample}>Load sample</button>
</div>

<Table words={words}/>

<style>

</style>
