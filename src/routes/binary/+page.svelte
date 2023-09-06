<script>
    import ImgBinaryB from "$lib/components/Img_binary_b.svelte";
    import ImgBinaryT from "$lib/components/Img_binary_t.svelte";
    import ImgClear from "$lib/assets/delete.png";
  

    var input ="Text";
    var output = "01010100 01100101 01111000 01110100";

    function convert(){
        output = "";
        for (var i = 0; i < input.length; i++) {
            output += input[i].charCodeAt(0).toString(2) + " ";
        }
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

            <textarea bind:value={input} class="input_input br bc_gray" id="input_text" rows="5" cols="33"></textarea>
            <button onclick="document.getElementById('input_text').value=''" class="del_btn br" ><img style="width: 20px;" src={ImgClear} alt="Clear normal"/></button>

        </div>
        
        <div class="change_box br">
            <button class="change_btn br bc_color" on:click={convert}></button>
        </div>
        
        <div class="output br">
            <h2>Binary</h2>

            <textarea bind:value={output} class="output_input br bc_gray" id="output_text" rows="5" cols="33"></textarea>
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

    .change_box {
        width: 100px;
        height: 100%;
        display: flex;
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