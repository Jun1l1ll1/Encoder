<script>
    import ImgBinaryB from "$lib/components/Img_binary_b.svelte";
import ImgBinaryT from "$lib/components/Img_binary_t.svelte";

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
            <textarea class="input_input br bc_gray" id="input_text" rows="5" cols="33">Text</textarea>
            <button onclick="document.getElementById('input_text').value=''" class="input_del br" >Clear</button>
        </div>
        
        <div class="change_box br">
            <button class="change_btn br bc_color"></button>
        </div>
        
        <div class="output br">
            <h2>Binary</h2>
            <textarea class="output_input br bc_gray" id="output_text" rows="5" cols="33">01010100 01100101 01111000 01110100</textarea>
            <button onclick="document.getElementById('output_text').value=''" class="output_del br">Clear</button>
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
        height: 300px;
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

    .input_del {
        height: 20px;
        background-color: red;
        position: absolute;
        right: 10px; 
        border: none;
    } .input_del:hover {
        background-color: tomato;
    } .input_del:active {
        background-color: red;
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
        height: 300px;
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

    .output_del {
        height: 20px;
        background-color: red;
        position: absolute;
        left: 10px;
        border: none;
    } .output_del:hover {
        background-color: tomato;
    } .output_del:active {
        background-color: red;
    }
</style>