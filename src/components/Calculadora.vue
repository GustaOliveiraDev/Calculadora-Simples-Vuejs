<template>
  <main>
    <div id="container">

      <div class="calculadora">

        <div class="display">
          <div class="operation">{{ getOperation }}</div>
          <div>{{ getResult }}</div>
        </div>

        <div class="botao zero" @click="Limpar()" >AC</div>
        <div class="botao " @click="LimparUnidade()" >DEL</div>
        <div class="botao operadores" @click="GetNumber('÷')" >÷</div>

        <div class="botao" @click="GetNumber('7')" >7</div>
        <div class="botao" @click="GetNumber('8')" >8</div>
        <div class="botao" @click="GetNumber('9')" >9</div>

        <div class="botao operadores"  @click="GetNumber('x')" >x</div>

        <div class="botao" @click="GetNumber('4')" >4</div>
        <div class="botao" @click="GetNumber('5')" >5</div>
        <div class="botao" @click="GetNumber('6')" >6</div>

        <div class="botao operadores"  @click="GetNumber('-')" >-</div>

        <div class="botao" @click="GetNumber('1')" >1</div>
        <div class="botao" @click="GetNumber('2')" >2</div>
        <div class="botao" @click="GetNumber('3')" >3</div>

        <div class="botao operadores" @click="GetNumber('+')" >+</div>

        <div class="botao zero" @click="GetNumber('0')" >0</div>

        <div class="botao" @click="GetNumber('.')" >.</div>
        <div class="botao operadores" @click="ClickResult()" > = </div>
      </div>
    </div>
  </main>
</template>

<script>


export default {

  data() {
    return {
      getOperation: '',
      getResult: '0',
    };
  },

  methods: {

    GetNumber(parms) {
      if(this.getResult == '0'){
        this.getResult = parms
      }else {
        this.getResult += parms
      }
    },

    ClickResult() {
      let result = this.getResult;
      this.getOperation = result;

      result = result.replace('x', '*')
      result = result.replace('-', '-')
      result = result.replace('+', '+')
      result = result.replace('÷', '/')

      this.getResult = eval(result);
    },
    
    Limpar() {
      this.getResult = '0'
      this.getOperation = ''
    },

    LimparUnidade() {
      if(this.getResult.length > 1){
        this.getResult = this.getResult.substring(0,  this.getResult.length - 1)
      }else{
        this.getResult = '0'
      }
    },


  },
}
</script>



<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins&display=swap');

* {
  font-family: Poppins;
}

#container {
  width: 100vw;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.calculadora {
  padding: 20px;
  margin: 0 auto;
  width: 350px;
  font-size: 40px;
  border-radius: 10px;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(50px, auto);
  background: #253046;
}

.display {
  grid-column: 1 / 5;
  background-color: #34425f;
  color: white;
  padding: 10px;
  margin-bottom: 10px;
  border-radius: 10px;
  display: flex;
  text-align: right;
  flex-direction: column;

}

.operation{
  font-size: 20px;
}

.zero {
  grid-column: 1 / 3;
}

.botao {
  margin: 5px;
  padding: 10px;
  display: flex;
  justify-content: center;
  background-color: #34425f;
  color: white;
  border-radius: 10px;
  cursor: pointer;
}

.operadores {
  background-color: #1bc887;
  color: white;
}
</style>
