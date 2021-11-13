<script>
  let result = 0;
  let state = null;
  let console = "";

  function resolveState() {
    switch (state) {
      case "plus":
        result += parseFloat(console);
        console = "0";
        break;
      case "minus":
        result -= parseFloat(console);
        console = "0";
        break;
      case "razy":
        result *= parseFloat(console);
        console = "0";
        break;
      case "dziel":
        result /= parseFloat(console);
        console = "0";
        break;
      default:
        result = parseFloat(console);
        console = "0";
        break;
    }
  }

  function setOperation(operation) {
    resolveState();
    state = operation;
  }

  function setValue(value) {
    if (console.toString() == "0" || state == "equal") {
      console = "";
    }
    if (state == "equal") {
      state = null;
    }
     if (value == "ac") {
      result = 0;
      console = "";
      state = null;
      return;
    }
    if (value == "C") {
      console = "0";
      return;
    }
    console = console + value;
  }

  function equal() {
    resolveState();
    console = result;
    state = "equal";
  }
</script>

<div class="calcdiv">
  <input type="text" bind:value={console}>
  <table>
   <tr>
      <td><button on:click={()=>{setValue('C');}}>C</button></td>
      <td><button on:click={()=>{setOperation('ac');}}>AC</button></td>
      <td><button on:click={()=>{setOperation('plm');}}>+/-</button></td>
      <td><button class="oper" on:click={()=>{setOperation('dziel');}}>/</button></td>
    </tr>
    <tr>
      <td><button on:click={()=>{setValue(1);}}>1</button></td>
      <td><button on:click={()=>{setValue(2);}}>2</button></td>
      <td><button on:click={()=>{setValue(3);}}>3</button></td>
      <td><button class="oper" on:click={()=>{setOperation('razy');}}>*</button></td>
    </tr>
    <tr>
      <td><button on:click={()=>{setValue(4);}}>4</button></td>
      <td><button on:click={()=>{setValue(5);}}>5</button></td>
      <td><button on:click={()=>{setValue(6);}}>6</button></td>
      <td><button class="oper" on:click={()=>{setOperation('plus');}}>+</button></td>
   
    </tr>
    <tr>
      <td><button on:click={()=>{setValue(7);}}>7</button></td>
      <td><button on:click={()=>{setValue(8);}}>8</button></td>
      <td><button on:click={()=>{setValue(9);}}>9</button></td>
      <td><button class="oper" on:click={()=>{setOperation('minus');}}>-</button></td>
      
      
    </tr>
    <tr>
      <td colspan="2" ><button class="zero" on:click={()=>{setValue(0);}}>0</button></td>
      <td><button on:click={()=>{setValue('.');}}>.</button></td>
      <td><button class="oper" on:click={equal}>=</button></td>
    </tr>
  </table>
</div>


<style>
  .calcdiv {
    width: 17rem;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    background: #262626;
    padding: 1rem;
    border-radius: 1rem;
    border:0;
  }

  button {
    border-radius: 1rem;
    border:0;
    width: 4rem;
    height: 4rem;
    font-size: large;
    font-family: "Franklin Gothic Medium", "Arial Narrow", Arial, sans-serif;
    background: #d9d9d9;
  }

  input {
    border-radius: 1rem;
    border:0;
    text-align: end;
    font-size: xx-large;
    width: 16.3rem;
    height: 3rem;
  }

  .oper{
    background: #1a8cff;
  }

  .zero{
    width: 8rem;
  }
</style>