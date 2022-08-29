<script>
    export let value;
    export let countWords;
    export let loadSample;
</script>

<div class="input">
    <textarea bind:value={value} placeholder="Enter text"></textarea>
    <button class="btn-filled" on:click={countWords}>Count words</button>
    <button class="btn-empty" on:click={loadSample}>Load sample</button>
</div>

<style>
    .input {
        background-color: #fff;
        padding: 35px 25px 25px;
        grid-area: input;
        position: relative;
    }

    .input:before {
        content: '';
        background: url('../assets/icons/keyboard.svg') no-repeat;
        width: 91px;
        height: 74px;
        position: absolute;
        right: -30px;
        top: -30px;
        transform: rotate(20deg);
    }

    textarea {
        font-family: 'Roboto Mono', sans-serif;
        width: 100%;
        min-height: 260px;
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