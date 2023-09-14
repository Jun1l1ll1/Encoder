<script>
    import ImgClear from "$lib/assets/trash.svg";

    const ALPHABETH = "ABCDEFGHIJKLMNOPQRSTUVWXYZÆØÅ";

    let input_text = "Convert whatever you want!";
    let output_text = "Eqpxgtv yjcvgxgt aqw ycpv!";

    // let change_to_ceasar = true;
    let shift_dir = "right";
    let shift_number = 2;
    let useÆØÅ = false;

    function shift() {
        let nr = shift_dir == "right" ? shift_number : -shift_number;
        let alph_len = useÆØÅ ? 29 : 26;

        let new_text = "";
        for (let i = 0; i < input_text.length; i++) {
            if (ALPHABETH.indexOf(input_text[i].toUpperCase()) == -1) { // Not in the alphabeth
                new_text += input_text[i];
            }
            else { // In the alphabeth
                let new_index = ALPHABETH.indexOf(input_text[i].toUpperCase()) + nr;
                if (new_index >= alph_len) { // Greater than the alphabeth
                    new_index -= alph_len;
                } else if (new_index < 0) { // Lower than the alphabeth
                    new_index += alph_len;
                }

                if (input_text[i] == input_text[i].toUpperCase()) { // Is upper case
                    new_text += ALPHABETH[new_index];
                } else { // Is lower case
                    new_text += ALPHABETH[new_index].toLowerCase();
                }
            }
        }
        
        output_text = new_text;
    }

    // function swap_dir() {
    //     change_to_ceasar = !change_to_ceasar;
    // }
</script>

<div class="center">

    <h1 class="title front">Caesar Cipher Converter</h1>

    <div>
        <div class="options_box br">
            <fieldset class="br bc_dark_gray">
                <legend>Direction</legend>
                <div>
                    <input bind:group={shift_dir} value="left" type="radio" name="dir" id="left"><label for="left">Left</label>
                    <input bind:group={shift_dir} value="right" type="radio" name="dir" id="right" checked><label for="right">Right</label>
                </div>
            </fieldset><br/>
            <fieldset class="br bc_dark_gray">
                <legend>Shift amount</legend>
                <input bind:value={shift_number} class="br bc_dark" style="border: none; padding: 5px; color:#00FF62;" type="number" placeholder="2">
            </fieldset>
            <fieldset class="br bc_dark_gray">
                <legend>ÆØÅ?</legend>
                <input bind:checked={useÆØÅ} type="checkbox" id="ÆØÅ"><label for="ÆØÅ">Use "æøå"</label>
            </fieldset>
        </div>

    
        <div class="input_grid_cont front">
    
            <div class="input br">
                <h2>Input</h2>
    
                <textarea bind:value={input_text} class="input_input br bc_gray" id="input_text" rows="5" cols="33"></textarea>
                <button onclick="document.getElementById('input_text').value=''" class="del_btn br" ><img style="width: 20px;" src={ImgClear} alt="Clear normal"/></button>
    
            </div>
            
            <div class="change_box br">
                <button class="change_btn br bc_color" on:click={shift}></button>
                <button class="dir_btn br">-&gt;</button>
            </div>
            
            <div class="output br">
                <h2>Output</h2>
    
                <textarea bind:value={output_text} class="output_input br bc_dark_gray" id="output_text" rows="5" cols="33" readonly></textarea>
                <!-- <button onclick="document.getElementById('output_text').value=''" class="del_btn br"><img style="width: 20px;" src={ImgClear} alt="Clear binary"/></button> -->
    
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
    input[type="radio"], input[type="checkbox"] {
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