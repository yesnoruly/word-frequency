<script>
    let text = '';
    let words = [];

    function countWords() {
        if (text) {
            words = text.split(' ');

            // Filter repeating words in array
            let wordsFiltered = [...new Set(words)];

            // Generate and sort array with objects
            words = wordsFiltered
                .map((word) => {
                    // Get the number of identical words
                    let num = words.filter(x => x === word).length;
                    return {word, num};
                })
                .sort((firstWord, secondWord) => secondWord.num - firstWord.num);
            }
    }

    function loadSample() {
        text = 'Disaster Baker hand rail deck boned out coffin rad fakie out. Kick-nose half-flip powerslide 900 Japan air slide Ed Templeton poseur. Full pipe hang-up birdie helipop masonite pressure flip aerial Rector. Pivot steps manual coffin heel flip stoked bail. Lip hurricane stalefish skate key sketchy opposite footed downhill. Casper noseblunt slide axle set camel back rock and roll acid drop risers. Rad locals masonite Cross Bones melancholy stoked steps 1080. Powell Peralta slappy axle set launch ramp nose grab g-turn lien air frontside. Roll-in 1080 cess slide axle full-cab kidney stoked. Sidewalk Surfer half-flip grab full pipe tail aerial nollie hospital flip. '
    }
</script>

<div class="wf">
    <textarea bind:value={text} id="textarea-freq" placeholder="Enter text"></textarea>
    <button on:click={countWords}>Count words</button>
    <button on:click={loadSample}>Load sample</button>
</div>

<ul>
    {#each words as {word, num}}
        <li>{word}: {num} times</li>
    {/each}
</ul>

<style>

</style>
