<!-- 
    input = normal text
    output = chypher
 -->

<div class="title">
    <h1>Binary converter</h1>
</div>

<div class="input br">
    <h2>Normal</h2>
    <textarea class="input_input br bc_gray" id="input_text" rows="5" cols="33">Normal text</textarea>
    <button onclick="document.getElementById('input_text').value=''" class="input_del br" >Clear</button>
</div>

<div class="change br bc_color">
    <button class="change_btn br bc_color"></button>
</div>

<div class="output br">
    <h2>Binary</h2>
    <textarea class="output_input br bc_gray" id="output_text" rows="5" cols="33">Binary</textarea>
    <button onclick="document.getElementById('output_text').value=''" class="output_del br">Clear</button>

</div>

<style>
    .title {
        position: absolute;
        top: 50px;
        left: 500px;
    }

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

    .change {
        width: 50px;
        height: 50px;
        position: absolute;
        top: 280px;
        left: 655px;
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