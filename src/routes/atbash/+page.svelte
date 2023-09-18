<script>
    
    import ImgClear from "$lib/assets/trash.svg";
  
    const ALPHABETH = "ABCDEFGHIJKLMNOPQRSTUVWXYZÆØÅ";

    var input ="Convert whatever you want!";
    var output = "Xlmevig dszgvevi blf dzmg!";

    var change_to_atbash = true;
    let useÆØÅ = false;

    function to_atbash() {
        let out = "";
        let alph_len = useÆØÅ ? 29-1 : 26-1;

        for (let letter of input) {
            if (ALPHABETH.indexOf(letter.toUpperCase()) == -1) {
                out += letter;
                continue;
            }

            let new_letter = ALPHABETH[alph_len - ALPHABETH.indexOf(letter.toUpperCase())];
            
            letter.toLowerCase() == letter ? new_letter = new_letter.toLowerCase() : "";
            out += new_letter;
        }

        output = out;
    }

    function to_norm() {
        let out = "";
        let alph_len = useÆØÅ ? 29-1 : 26-1;

        for (let letter of output) {
            if (ALPHABETH.indexOf(letter.toUpperCase()) == -1) {
                out += letter;
                continue;
            }

            let new_letter = ALPHABETH[alph_len - ALPHABETH.indexOf(letter.toUpperCase())];
            
            letter.toLowerCase() == letter ? new_letter = new_letter.toLowerCase() : "";
            out += new_letter;
        }

        input = out;
    }


    function swap_dir() {
        change_to_atbash = !change_to_atbash
    }


</script>
<!-- 
    input = normal text
    output = chypher
-->

<div class="center">
    <h1 class="title front">Atbash converter</h1>
    <div>
        <div class="options_box br">
            <fieldset class="br bc_dark_gray">
                <legend>ÆØÅ?</legend>
                <input bind:checked={useÆØÅ} type="checkbox" id="ÆØÅ"><label for="ÆØÅ">Use "æøå"</label>
            </fieldset>
        </div>

        <div class="input_grid_cont front">
    
            <div class="input br">
                <h2>Text</h2>
    
                <textarea bind:value={input} class="input_input br bc_gray" id="input_text" rows="5" cols="33"></textarea>
                <button onclick="document.getElementById('input_text').value=''" class="del_btn br" ><img style="width: 20px;" src={ImgClear} alt="Clear normal"/></button>
    
            </div>
            
            <div class="change_box br">
                <button class="change_btn br bc_color" on:click={() => {change_to_atbash ? to_atbash() : to_norm()}}></button>
                <button on:click={swap_dir} class="dir_btn br">{#if change_to_atbash}-&gt;{:else}&lt;-{/if}</button>
            </div>
            
            <div class="output br">
                <h2>Atbash</h2>
    
                <textarea bind:value={output} class="output_input br bc_gray" id="output_text" rows="5" cols="33"></textarea>
                <button onclick="document.getElementById('output_text').value=''" class="del_btn br"><img style="width: 20px;" src={ImgClear} alt="Clear binary"/></button>
    
            </div>
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

    .options_box {
        margin-top: 25px;
        padding: 10px;
        width: fit-content;
        display: flex;
    }
    .options_box fieldset {
        border: none;
        margin-right: 50px;
    }
    input[type="checkbox"] {
        accent-color: #00FF62;
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