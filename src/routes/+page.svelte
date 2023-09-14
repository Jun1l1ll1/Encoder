<script>
    import Icons from "$lib/components/Icons.svelte";

    let ciphers = {
        "Binary": {"icon":"binary", "txt":"01000010 01101001 01101110 01100001 01110010 01111001 00100000 01100011 01101111 01100100 01100101"},
        "Morse": {"icon":"morse", "txt":"-- --- .-. ... .  -.-. --- -.. ."},
        "Caesar Cipher": {"icon":"caesar", "txt":"Eqpxgtv cpavjkpi vq ecguct ekrjgt"},
        "a1z26": {"icon":"a1z26", "txt":"3 15 14 22 5 18 20  20 5 24 20  20 15  14 21 13 2 5 18 19"},
    }

</script>


<div class="center">

    <h1 class="title front">The Ultimate Encoder</h1>

    <div class="grid">
        {#each Object.keys(ciphers) as cipher}
        <div class="grid_element br bc_dark_gray">
            <h3 class="cipher_title">{cipher}</h3>
            <div class="cipher_text">{ciphers[cipher]["txt"]}</div>
            <div class="cipher_icon"><Icons cypher={ciphers[cipher]["icon"]} color="#00FF62" is_static=true/></div>
            <button class="go_to_btn br bc_color">&lt;</button>
        </div>
        {/each}
    </div>
    
</div>


<style>
    .front {
        z-index: 1;
    }

    .center {
        width: calc(100% - 71px);
        height: 100%;
        position: absolute;
        /* border: 1px red solid; */
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    .title {
        margin-top: 75px;
    }

    .grid {
        display:grid; 
        grid-template-columns: auto auto auto;
        grid-gap: 50px;
        margin-top: 50px;
    }

    .grid_element {
        width: 300px;
        height: 200px;
        position: relative;
    }


    .cipher_title {
        margin-left: 15px;
        margin-bottom: 0px;
        color: #00FF62;
    }

    .cipher_text {
        position: absolute;
        margin: 15px;
    }
    
    .cipher_icon {
        width: 75px;
        aspect-ratio: 1/1;
        position: absolute;
        display: flex;
        justify-content: center;
        align-items: center;
        right: 0px;
        bottom: 0px;
    }

    .go_to_btn {
        border: none;
        width: 50%;
        height: 40px;
        position: absolute;
        bottom: 0px;
        transition: .25s;

        text-align: left;
        font-size: larger;
    }
    .go_to_btn:hover {
        background-color: lightgreen;
    }

</style>