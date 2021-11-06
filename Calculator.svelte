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
    if (value == "C") {
      result = 0;
      console = "";
      state = null;
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
      <td><button on:click={()=>{setValue(1);}}>1</button></td>
      <td><button on:click={()=>{setValue(2);}}>2</button></td>
      <td><button on:click={()=>{setValue(3);}}>3</button></td>
      <td><button on:click={()=>{setValue('C');}}>C</button></td>
    </tr>
    <tr>
      <td><button on:click={()=>{setValue(4);}}>4</button></td>
      <td><button on:click={()=>{setValue(5);}}>5</button></td>
      <td><button on:click={()=>{setValue(6);}}>6</button></td>
      <td><button on:click={()=>{setValue('.');}}>.</button></td>
    </tr>
    <tr>
      <td><button on:click={()=>{setValue(7);}}>7</button></td>
      <td><button on:click={()=>{setValue(8);}}>8</button></td>
      <td><button on:click={()=>{setValue(9);}}>9</button></td>
      <td><button on:click={equal}>=</button></td>
      
    </tr>
    <tr>
      <td><button on:click={()=>{setOperation('plus');}}>+</button></td>
      <td><button on:click={()=>{setOperation('minus');}}>-</button></td>
      <td><button on:click={()=>{setOperation('razy');}}>*</button></td>
      <td><button on:click={()=>{setOperation('dziel');}}>/</button></td>
    </tr>
  </table>
</div>


<style>
  .calcdiv {
    width: 20rem;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
  }

  button {
    width: 4rem;
    height: 3rem;
    font-size: large;
    font-family: "Franklin Gothic Medium", "Arial Narrow", Arial, sans-serif;
  }

  input {
    width: 16rem;
    height: 2rem;
  }
</style>