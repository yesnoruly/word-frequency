<script>
    let paragraph = '';
    let words = [];

    function countWords() {
        if (paragraph) {
            words = paragraph.split(' ')
            console.log(words)
        }
    }

    function loadSample() {
        paragraph = 'Disaster Baker hand rail deck boned out coffin rad fakie out. Kick-nose half-flip powerslide 900 Japan air slide Ed Templeton poseur. Full pipe hang-up birdie helipop masonite pressure flip aerial Rector. Pivot steps manual coffin heel flip stoked bail. Lip hurricane stalefish skate key sketchy opposite footed downhill. Casper noseblunt slide axle set camel back rock and roll acid drop risers. Rad locals masonite Cross Bones melancholy stoked steps 1080. Powell Peralta slappy axle set launch ramp nose grab g-turn lien air frontside. Roll-in 1080 cess slide axle full-cab kidney stoked. Sidewalk Surfer half-flip grab full pipe tail aerial nollie hospital flip. '
    }
</script>

<div class="wf">
    <textarea bind:value={paragraph} id="textarea-freq" placeholder="Enter text"></textarea>
    <button on:click={countWords}>Count words</button>
    <button on:click={loadSample}>Load sample</button>
</div>

<div>{words}</div>

<style>

</style>
