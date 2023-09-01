<!-- 
    input = normal text
    output = chypher
 -->

<div class="input br">
    <textarea class="input_input br bc_gray" id="input_text" rows="5" cols="33">Normal text</textarea>
    <button onclick="document.getElementById('input_text').value=''" class="input_del br" >Clear</button>
</div>

<div class="output br">
    <textarea class="output_input br bc_gray" id="output_text" rows="5" cols="33">Binary</textarea>
    <button onclick="document.getElementById('output_text').value=''" class="output_del br">Clear</button>

</div>

<style>
    .input {
        height: 200px;
        width: 400px;
        position: absolute;
        top: 150px;
        left: 200px;
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

    .output {
        height: 200px;
        width: 400px;
        position: absolute;
        top: 150px;
        right: 200px;
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