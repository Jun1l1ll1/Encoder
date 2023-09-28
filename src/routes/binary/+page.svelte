<script>
    import ImgBinaryB from "$lib/components/Img_binary_b.svelte";
    import ImgBinaryT from "$lib/components/Img_binary_t.svelte";
    import ImgClear from "$lib/assets/Trash.svg";
    import ChangeDirArrow from "$lib/components/Change_dir_arrow.svelte";

    import autosize from 'svelte-autosize';
    import {tick} from 'svelte';
  

    var input = "Text";
    var output = "01010100 01100101 01111000 01110100";

    var change_to_binary = true;

    let output_size = ""
    let input_size = ""

    async function resize() {
        await tick();
        autosize.update(output_size);
        autosize.update(input_size);
    }

    function to_binary() {
        output = "";
        for (var i = 0; i < input.length; i++) {
            output += (0b100000000 + input[i].charCodeAt(0)).toString(2).substring(1) + " ";
        }
    }

    function normal(output) {
        var bin_string = "";

        output.split(" ").map(function(bin) {
            bin_string += String.fromCharCode(parseInt(bin, 2));
        });
        return bin_string;
    }

    function to_norm() {
        input = ""
        input = normal(output)
        autosize.update(input)
    }

    function swap_dir() {
        change_to_binary = !change_to_binary
    }

</script>
<!-- 
    input = normal text
    output = chypher
-->

<div class="center">
    <ImgBinaryT/>
    <ImgBinaryB/>

    <h1 class="title front">Binary converter</h1>

    <div class="input_grid_cont front">

        <div class="input br">
            <h2>Text</h2>

            <textarea bind:value={input} bind:this={input_size} use:autosize class="input_input br bc_gray" id="input_text" rows="5" cols="33"></textarea>
            <button onclick="document.getElementById('input_text').value=''" class="del_btn br" ><img style="width: 20px;" src={ImgClear} alt="Clear normal"/></button>

        </div>
        
        <div class="change_box br">
            <button class="change_btn br bc_color" on:click={() => {change_to_binary ? to_binary() : to_norm()}} on:click={resize}></button>
            <button on:click={swap_dir} class="dir_btn br"><ChangeDirArrow right={change_to_binary}/></button>
        </div>
        
        <div class="output br">
            <h2>Binary</h2>

            <textarea bind:value={output} bind:this={output_size} use:autosize class="output_input br bc_gray" id="output_text" rows="5" cols="33"></textarea>
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
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    @media screen and (min-width: 700px) {
        .input_grid_cont {
            display:grid; 
            grid-template-columns: auto auto auto;
        }
    }

    @media screen and (max-width: 700px) {
        .input_grid_cont {
            display:grid; 
            grid-template-columns: auto;
        }
    }

    .title {
        margin-top: 75px;
        text-align: center;
    }

    @media screen and (min-width: 700px) {
        .input {
            width: 400px;
            height: fit-content;
            position: relative;
        }
    }

    @media screen and (max-width: 700px) {
        .input {
            width: 200px;
            height: fit-content;
            position: relative;
        }
    }

    @media screen and (min-width: 700px) {
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
    }

    @media screen and (max-width: 700px) {
        .input_input {
            height: 150px;
            min-height: 150px;
            width: 250px;
            max-width: 250px;
            min-width: 250px;
            border: none;
            color: white;
            font-family: "input-mono";
        }
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
    
    @media screen and (min-width: 700px) {
        .change_box {
            width: 100px;
            height: 100%;
            display: flex;
            flex-direction: column;
            padding-top: 120px;
            align-items: center;
        }
    }

    @media screen and (max-width: 700px) {
        .change_box {
            width: 100px;
            height: 100%;
            display: flex;
            flex-direction: row;
            justify-content: center;
            align-items: center;
        }
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

    @media screen and (min-width: 700px) {
        .output {
            width: 400px;
            height: fit-content;
            position: relative;
        }
    }

    @media screen and (max-width: 700px) {
        .output {
            width: 200px;
            height: fit-content;
            position: relative;
        }
    }

    @media screen and (min-width: 700px) {
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
    }

    @media screen and (max-width: 700px) {
        .output_input {
            height: 150px;
            min-height: 150px;
            width: 250px;
            max-width: 250px;
            min-width: 250px;
            border: none;
            color: white;
            font-family: "input-mono";
        } 
    }
</style>