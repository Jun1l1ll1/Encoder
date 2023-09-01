<div class="input br bc_gray">
    <input type="text" class="input_input br bc_gray">
    
</div>
<button class="input_del br">Delete input</button>

<div class="output br bc_gray">
    <input type="text" class="output_input br bc_gray">

</div>
<button class="output_del br">Delete output</button>

<style>
    .input {
        height: 200px;
        width: 400px;;
        position: absolute;
        top: 150px;
        left: 200px;
    }

    .input_input {
        height: 200px;
        width: 400px;
        border: none;
        color: white;
    }

    .input_del {
        height: 20px;
        background-color: red;
        position: absolute;
        top: 360px;
        left: 500px;
        border: none;
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
        width: 400px;
        border: none;
        color: white;
    }

    .output_del {
        height: 20px;
        background-color: red;
        position: absolute;
        top: 360px;
        right: 490px;
        border: none;
    }
</style>