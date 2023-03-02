<script setup>
import {ref, computed} from 'vue';
  const nex = "Nex";

  //Variable reactiva
  const counter = ref(0);

  const arrayFavoritos = ref([])



  const incremento = () => {
    counter.value ++;
  }
  const decremento = () => {
    counter.value --;
  }
  const reseteo = () => {
    counter.value = 0;
  }

  const add = () => { 
    arrayFavoritos.value.push(counter.value)

  }

  const bloquearBtnAdd = computed(() => {
    //find busca un elemento dentro del array
    const numSearch = arrayFavoritos.value.find(num => num === counter.value);
    if(numSearch === 0) return true;
    return numSearch ? true : false;
  })

  const classCounter = computed(() => {
    if(counter.value === 0) {
      return 'zero'
    }
    if (counter.value > 0) {
      return 'positivo'
    }
    if (counter.value < 0) {
      return 'negativo'
    }

  })

</script>

<template>
  <div class="flex">
    <img class="flex-chefCito" src="./assets/img/nexChef.png">
    <h1 class="flex-h1">Hola {{ nex.toUpperCase() }}</h1>
  </div>
  <hr>
  <!-- Manera del profe -->
  <h2 :class="classCounter">{{ counter }}</h2>
  <!--  -->

  <button v-on:click="incremento">
    <span>Aumentar</span>
  </button>
  <button v-on:click="decremento">
    <span>Disminuir</span>
  </button>
  <button v-on:click="reseteo">
    <span>Reseteo</span>
  </button>
  <button v-on:click="add" :disabled="bloquearBtnAdd">
    <span>Agregar</span>
  </button> <br>
  <ul>
    <li
    v-for="(num, index) in arrayFavoritos" :key="index">
    {{ num }}
    </li>
  </ul>




</template>



<style>


.flex {
  display: flex;
  align-items: center;
}
.flex-chefCito {
  width: 70px;
}
.flex-h1 {
  color: rgb(76, 255, 177);
  font-style: initial;
  font-family: 'Times New Roman', Times, serif;
  text-align: center;
}



/* Manera del profe */

.positivo {
  color: green;
}
.negativo {
  color: red;
}
.zero{
  color: peru;
}

/* button {
  padding: 0.1em 0.25em;
  width: 13em;
  height: 4.2em;
  background-color: #212121;
  border: 0.08em solid #fff;
  border-radius: 0.3em;
  font-size: 12px;
}

button span {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  bottom: 0.4em;
  width: 8.25em;
  height: 2.5em;
  background-color: #212121;
  border-radius: 0.2em;
  font-size: 1.5em;
  color: #fff;
  border: 0.08em solid #fff;
  box-shadow: 0 0.4em 0.1em 0.019em #fff;
}

button:focus span {
  transition: all 0.1s;
  transform: translate(0, 0.4em);
  box-shadow: 0 0 0 0 #fff;
}

button span:not(focus) {
  transition: all 0.1s;
} */

</style>