<script>
    import ImgA1z26T from "$lib/components/Img_a1z26_t.svelte";
    import ImgA1z26B from "$lib/components/Img_a1z26_b.svelte";
    import ImgClear from "$lib/assets/Trash.svg";
    import ChangeDirArrow from "$lib/components/Change_dir_arrow.svelte";

    import autosize from 'svelte-autosize';
    import {tick} from 'svelte';
  
    var input ="Text";
    var output = "20 5 24 20";

    var change_to_a1z26 = true;

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

    let norm_to_a1z26 = {
        a: "1",
        b: "2",
        c: "3",
        d: "4",
        e: "5",
        f: "6",
        g: "7",
        h: "8",
        i: "9",
        j: "10",
        k: "11",
        l: "12",
        m: "13",
        n: "14",
        o: "15",
        p: "16",
        q: "17",
        r: "18",
        s: "19",
        t: "20",
        u: "21",
        v: "22",
        w: "23",
        x: "24",
        y: "25",
        z: "26",
        æ: "27",
        ø: "28",
        å: "29",
        1: "number",
        2: "number",
        3: "number",
        4: "number",
        5: "number",
        6: "number",
        7: "number",
        8: "number",
        9: "number",
        0: "number"
    }

    function to_a1z26() {
        let out = "";
        for (let i = 0; i < input.length; i++) {
            if (input[i] == " ") {
                out += " ";
            } else if ((norm_to_a1z26[input[i].toLocaleLowerCase()]) == undefined){
                out += input[i] + " ";
            } else {
                out += norm_to_a1z26[input[i].toLocaleLowerCase()] + " ";
            }
        }
        output = out;
    }

    function to_norm() {
        let a1z26_list = output.split(" ")
        let out = "";
        for (let i = 0; i < a1z26_list.length; i++) {
            if (a1z26_list[i] == "") {
                out += " "
            } else if ((get_key_by_value(norm_to_a1z26, a1z26_list[i])) == undefined){
                out += a1z26_list[i]
            } else {
                out += get_key_by_value(norm_to_a1z26, a1z26_list[i]);
            }
        }
        input = out;
    }

    function swap_dir() {
        change_to_a1z26 = !change_to_a1z26;
    }


</script>

<!-- 
    input = normal text
    output = chypher
-->

<div class="center">
    <ImgA1z26T/>
    <ImgA1z26B/>

    <h1 class="title front">a1z26 converter</h1>

    <div class="input_grid_cont front">

        <div class="input br">
            <h2>Text</h2>

            <textarea bind:value={input} bind:this={input_size} use:autosize class="input_input br bc_gray" id="input_text" rows="5" cols="33"></textarea>
            <button onclick="document.getElementById('input_text').value=''" class="del_btn br" ><img style="width: 20px;" src={ImgClear} alt="Clear normal"/></button>

        </div>
        
        <div class="change_box br">
            <button class="change_btn br bc_color" on:click={() => {change_to_a1z26 ? to_a1z26() : to_norm()}} on:click={resize}></button>
            <button on:click={swap_dir} class="dir_btn br"><ChangeDirArrow right={change_to_a1z26}/></button>
        </div>
        
        <div class="output br">
            <h2>a1z26</h2>

            <textarea bind:value={output} bind:this={output_size} use:autosize class="output_input br bc_gray" id="output_text" rows="5" cols="33"></textarea>
            <button onclick="document.getElementById('output_text').value=''" class="del_btn br"><img style="width: 20px;" src={ImgClear} alt="Clear a1z26"/></button>

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