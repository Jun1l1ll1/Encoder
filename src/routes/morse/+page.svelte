<script>
    import ImgMorseT from "$lib/components/Img_morse_t.svelte";
    import ImgMorseB from "$lib/components/Img_morse_b.svelte";
    import ImgClear from "$lib/assets/Trash.svg";
    import ChangeDirArrow from "$lib/components/Change_dir_arrow.svelte";

    import autosize from 'svelte-autosize';
    import {tick} from 'svelte';

    let normal_inp = "Convert whatever you want!";
    let morse_inp = "-.-. --- -. ...- . .-. -  .-- .... .- - . ...- . .-.  -.-- --- ..-  .-- .- -. - -.-.--";

    let change_to_morse = true;

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

    let norm_to_morse = {
        a: ".-",
        b: "-...",
        c: "-.-.",
        d: "-..",
        e: ".",
        f: "..-.",
        g: "--.",
        h: "....",
        i: "..",
        j: ".---",
        k: "-.-",
        l: ".-..",
        m: "--",
        n: "-.",
        o: "---",
        p: ".--.",
        q: "--.-",
        r: ".-.",
        s: "...",
        t: "-",
        u: "..-",
        v: "...-",
        w: ".--",
        x: "-..-",
        y: "-.--",
        z: "--..",
        æ: ".-.-",
        ø: "---.",
        å: ".--.-",
        1: ".----",
        2: "..---",
        3: "...--",
        4: "....-",
        5: ".....",
        6: "-....",
        7: "--...",
        8: "---..",
        9: "----.",
        0: "-----",
        ".": ".-.-.-",
        "?": "..--..",
        "!": "-.-.--",
        ",": "--..--",
        ";": "-.-.-.",
        ":": "---...",
        "+": ".-.-.",
        "-": "-....-",
        "/": "-..-.",
        "=": "-...-",
        "\"": ".-..-.",
        "@": ".--.-.",
        "$": "...-..-",
        "_": "..--.-"
    }

    function to_morse() {
        let out = "";
        for (let i = 0; i < normal_inp.length; i++) {
            if (normal_inp[i] == " ") {
                out += " ";
            } else {
                out += norm_to_morse[normal_inp[i].toLocaleLowerCase()] + " ";
            }
        }
        morse_inp = out;
    }

    function to_norm() {
        let morse_list = morse_inp.split(" ")
        let out = "";
        for (let i = 0; i < morse_list.length; i++) {
            if (morse_list[i] == "") {
                out += " "
            } else {
                out += get_key_by_value(norm_to_morse, morse_list[i]);
            }
        }
        normal_inp = out;
    }

    function swap_dir() {
        change_to_morse = !change_to_morse;
    }

</script>
<!-- 
    input = normal text
    output = chypher
-->


<div class="center">
    <ImgMorseT/>
    <ImgMorseB/>

    <h1 class="title front">Morse converter</h1>

    <div class="input_grid_cont front">

        <div class="input br">
            <h2>Text</h2>
            <textarea bind:value={normal_inp} bind:this={input_size} use:autosize class="input_input br bc_gray" id="input_text" rows="5" cols="33"></textarea>
            <button onclick="document.getElementById('input_text').value=''" class="del_btn br" ><img style="width: 20px;" src={ImgClear} alt="Clear normal"/></button>
        </div>
        
        <div class="change_box br">
            <button on:click={() => {change_to_morse ? to_morse() : to_norm()}} on:click={resize} class="change_btn br bc_color"></button>
            <button on:click={swap_dir} class="dir_btn br"><ChangeDirArrow right={change_to_morse}/></button>
        </div>
        
        <div class="output br">
            <h2>Morse</h2>
            <textarea bind:value={morse_inp} bind:this={output_size} use:autosize class="output_input br bc_gray" id="output_text" rows="5" cols="33"></textarea>
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
        padding-top: 120px;
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