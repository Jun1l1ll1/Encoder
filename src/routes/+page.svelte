<script>
    import { goto } from '$app/navigation';
    import ChangeDirArrow from '$lib/components/Change_dir_arrow.svelte';

    import Icons from "$lib/components/Icons.svelte";

    let ciphers = {
        "!\"#¤ Cipher": {"code":"qwer", "txt":"£)n$#¤% /2(n5 ! 2&2%#{!%(£ #n£)3(n5 )n %6# 8#&b)!¤3"},
        "a1z26": {"code":"a1z26", "txt":"3 15 14 22 5 18 20  20 5 24 20  20 15  14 21 13 2 5 18 19"},
        "Atbash": {"code":"atbash", "txt":"Xlmevig gvcg drgs Zgyzhs xrksvi"},
        "Binary": {"code":"binary", "txt":"01000010 01101001 01101110 01100001 01110010 01111001 00100000 01100011 01101111 01100100 01100101"},
        "Caesar Cipher": {"code":"caesar", "txt":"Eqpxgtv cpavjkpi vq ecguct ekrjgt"},
        "Morse": {"code":"morse", "txt":"-- --- .-. ... .  -.-. --- -.. ."},
    }

</script>


<div class="center">

    <h1 class="title front">The Ultimate Encoder</h1>

    <div class="grid">
        {#each Object.keys(ciphers) as cipher}
        <div class="grid_element br bc_dark_gray">
            <h3 class="cipher_title">{cipher}</h3>
            <div class="cipher_text">{ciphers[cipher]["txt"]}</div>
            <div class="cipher_icon"><Icons cypher={ciphers[cipher]["code"]} color="#00FF62" is_static=true/></div>
            <button on:click={() => {goto("/"+ciphers[cipher]["code"])}} class="go_to_btn br bc_color"><ChangeDirArrow right={false} color="black"/></button>
        </div>
        {/each}
    </div>

    <!-- The ability to scroll further down than the elements -->
    <div style="margin-top: 100px; opacity: 0;">.</div>
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
        aspect-ratio: 3/2;
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