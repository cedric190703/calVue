<template>
  <div class="home">
    <h1 id="res"> {{ element }} </h1>
    <button class="btn" id="9" @click="equal == false ? element+='9': begin('9')">9</button>
    <button class="btn" id="8" @click="equal == false ? element+='8': begin('8')">8</button>
    <button class="btn" id="7" @click="equal == false ? element+='7': begin('7')">7</button>
    <button class="btn" id="6" @click="equal == false ? element+='6': begin('6')">6</button>
    <button class="btn" id="5" @click="equal == false ? element+='5': begin('5')">5</button>
    <button class="btn" id="4" @click="equal == false ? element+='4': begin('4')">4</button>
    <button class="btn" id="3" @click="equal == false ? element+='3': begin('3')">3</button>
    <button class="btn" id="2" @click="equal == false ? element+='2': begin('2')">2</button>
    <button class="btn" id="1" @click="equal == false ? element+='1': begin('1')">1</button>
    <button class="btn" id="0" @click="equal == false ? element+='0': begin('0')">0</button>
    <button class="btn" id="+" @click="equal == false ? element+='+': begin('+')">+</button>
    <button class="btn" id="*" @click="equal == false ? element+='*': begin('*')">*</button>
    <button class="btn" id="-" @click="equal == false ? element+='-': begin('-')">-</button>
    <button class="btn" id="." @click="equal == false ? element+='.': begin('.')">.</button>
    <button class="btn" id="/" @click="equal == false ? element+='/': begin('/')">/</button>
    <button id="equal" @click="calcul">=</button>
    <button id="reset" @click="reset">C</button>
  </div>
</template>

<script>
// @ is an alias to /src'
import {ref} from "vue";

export default {
  name: 'HomeView',
  setup() {
    const result = ref("");
    const element = ref("");
    const equal = ref(false);

    const begin = (val) => {
      element.value = val;
      equal.value = false;
    }

    const calcul = ()  => {
      equal.value = true;
      element.value = eval(element.value);
    }

    const reset = () => {
      result.value = '';
      element.value = '';
    }
    
    return{
      result,
      element,
      calcul,
      reset,
      equal,
      begin
    }
  }
}
</script>

<style>
  body {
    background: rgb(195,12,12);
    background: linear-gradient(90deg, rgba(195,12,12,0.7679446778711485) 0%, rgba(34,44,121,0.8883928571428571) 100%);
  }

  .home {
    background-color: white;
    height: 650px;
    margin: 8% 28%;
    border-radius: 25px;
    box-shadow: 10px 10px 37px 0px rgba(255,255,255,0.75);
    -webkit-box-shadow: 10px 10px 37px 0px rgba(255,255,255,0.75);
    -moz-box-shadow: 10px 10px 37px 0px rgba(255,255,255,0.75);
  }
  
  .home {
    color: white;
    position: relative;    
    background-color: #1a1d2a;
    display: grid;
    margin: 0 auto;
    grid-template-columns: 25% 25% 25% 25%;
    grid-template-rows: 120px repeat(5,100px);
    grid-template-areas: 
        "res res res res"
        "9 8 7 C"
        "6 5 4 C"
        "3 2 1 C"
        "0 dot mult plus"
        "equal equal minus div";
    margin: 8% 25%;
  }

  #equal {
    grid-area: equal;
  }
  
  #reset {
    grid-area: C;
  }

  #res {
    grid-area: res;
    text-align: right;
    padding: 2%;
  }

  button {
    font-size: x-large;
    border: 1px solid white;
    background-color: #1a1d2a;
    color: white;
    transition: all 0.5s ease-out;
  }

  button:hover {
    transform: scale(1.12);
  }

  @media screen and (max-width: 1300px) {
    .home {
      margin: 8% 10%;
    }
  }

  @media screen and (max-width: 1000px) {
    .home {
      margin: 15% 10%;
    }
  }

  @media screen and (max-width: 650px) {
    .home {
      margin: 20% 1%;
    }
  }
</style>
