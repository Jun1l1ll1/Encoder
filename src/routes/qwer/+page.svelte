<script>
    import ImgClear from "$lib/assets/Trash.svg";
    import ChangeDirArrow from "$lib/components/Change_dir_arrow.svelte";

    import autosize from 'svelte-autosize';
    import {tick} from 'svelte';

    let normal_inp = "Convert whatever you want!";
    let qwer_inp = "£)n$#¤% \"6!%#$#¤ &)/ \"!n%|";

    let change_to_qwer = true;

    let output_size = ""
    let input_size = ""

    async function resize() {
        await tick();
        autosize.update(output_size);
        autosize.update(input_size);
    }

    function get_key_by_value(obj, value) {
        return Object.keys(obj).find(key => obj[key] === value);
    }

    let norm_to_qwer = {
        a: "!",
        b: "b",
        c: "£",
        d: "3",
        e: "#",
        f: "4",
        g: "5",
        h: "6",
        i: "(",
        j: "7",
        k: "8",
        l: "9",
        m: "{",
        n: "n",
        o: ")",
        p: "=",
        q: "!",
        r: "¤",
        s: "2",
        t: "%",
        u: "/",
        v: "$",
        w: "\"",
        x: "@",
        y: "&",
        z: "z",
        æ: "+",
        ø: "0",
        å: "?",
        1: "illegal",
        2: "illegal",
        3: "illegal",
        4: "illegal",
        5: "illegal",
        6: "illegal",
        7: "illegal",
        8: "illegal",
        9: "illegal",
        0: "illegal",
        "?": "§",
        "!": "|",
        "\"": "illegal",
        "@": "illegal",
        "#": "illegal",
        "£": "illegal",
        "¤": "illegal",
        "$": "illegal",
        "%": "illegal",
        "&": "illegal",
        "/": "illegal",
        "{": "illegal",
        "(": "illegal", // Not really illegal, just hard to deal with
        ")": "illegal", // ^same
        "=": "illegal",
        "+": "illegal",
    }

    function to_qwer() {
        let out = "";
        for (let i = 0; i < normal_inp.length; i++) {
            if (norm_to_qwer[normal_inp[i].toLocaleLowerCase()] == undefined) {
                out += normal_inp[i];
            } else {
                out += norm_to_qwer[normal_inp[i].toLocaleLowerCase()];
            }
        }
        qwer_inp = out;
    }

    function to_norm() {
        let qwer_list = qwer_inp.split("")
        let out = "";
        for (let i = 0; i < qwer_list.length; i++) {
            if (get_key_by_value(norm_to_qwer, qwer_list[i]) == undefined) {
                out += qwer_list[i];
            } else {
                out += get_key_by_value(norm_to_qwer, qwer_list[i]);
            }
        }
        normal_inp = out;
    }

    function swap_dir() {
        change_to_qwer = !change_to_qwer;
    }

</script>
<!-- 
    input = normal text
    output = chypher
-->


<div class="center">

    <h1 class="title front">!"#¤ Cipher</h1>

    <div class="input_grid_cont front">

        <div class="input br">
            <h2>Text</h2>
            <textarea bind:value={normal_inp} bind:this={input_size} use:autosize class="input_input br bc_gray" id="input_text" rows="5" cols="33"></textarea>
            <button onclick="document.getElementById('input_text').value=''" class="del_btn br" ><img style="width: 20px;" src={ImgClear} alt="Clear normal"/></button>
        </div>
        
        <div class="change_box br">
            <button on:click={() => {change_to_qwer ? to_qwer() : to_norm()}} on:click={resize} class="change_btn br bc_color"></button>
            <button on:click={swap_dir} class="dir_btn br"><ChangeDirArrow right={change_to_qwer}/></button>
        </div>
        
        <div class="output br">
            <h2>!"#¤</h2>
            <textarea bind:value={qwer_inp} bind:this={output_size} use:autosize class="output_input br bc_gray" id="output_text" rows="5" cols="33"></textarea>
            <button onclick="document.getElementById('output_text').value=''" class="del_btn br"><img style="width: 20px;" src={ImgClear} alt="Clear binary"/></button>
        </div>
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

    .input_grid_cont {
        display:grid; 
        grid-template-columns: auto auto auto;
    }

    .title {
        margin-top: 75px;
    }

    .input {
        width: 400px;
        height: fit-content;
        position: relative;
    }

    .input_input {
        height: 200px;
        min-height: 200px;
        width: 400px;
        max-width: 400px;
        min-width: 400px;
        border: none;
        color: white;
        font-family: "input-mono";
    }

    .del_btn {
        padding: 5px;
        position: absolute;
        left: 10px;
        bottom: 10px;
        border: none;
        transition: .25s;
        background-color: rgba(0,0,0,0);
    } .del_btn:hover {
        background-color: rgb(163, 8, 41);
    } .del_btn:active {
        background-color: rgb(92, 0, 23);
    }

    .dir_btn {
        border: none;
        background-color: rgba(0,0,0,0);
        color: white;
        font-size: large;
        transition: .25s;
        margin-top: 10px;
    } .dir_btn:hover {
        background-color: #00FF62;
    }

    .change_box {
        width: 100px;
        height: 100%;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }

    .change_btn {
        width: 50px;
        height: 50px;
        border: none;
    } .change_btn:hover {
        background-color: lightgreen;
    } .change_btn:active {
        background-color: #00FF62;
    }

    .output {
        width: 400px;
        height: fit-content;
        position: relative;
    }

    .output_input {
        height: 200px;
        min-height: 200px;
        width: 400px;
        max-width: 400px;
        min-width: 400px;
        border: none;
        color: white;
        font-family: "input-mono";
    } 
</style>