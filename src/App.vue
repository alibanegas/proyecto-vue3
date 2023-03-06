<script setup>
import {ref, computed} from 'vue';

const name1 = "Vue dinamico";

const counter = ref(0);


const increment =() => {
    console.log('Aumentar Contador');
    counter.value ++;
};

const decrement =() => {
    console.log('Disminuir Contador');
    counter.value --;
}

const reset =() => {
    console.log('Resetear Contador');
    counter.value = 0;
}

const classCounter = computed(() => {
    if (counter.value === 0){
        return 'zero';
    }
    if (counter.value > 0){
        return 'positive';
    }
    if (counter.value < 0){
        return 'negative';
    }
} )

const arrayFavorite =ref([]);

const add = () => {
    arrayFavorite.value.push(counter.value);
};

const bloquearBtnAdd = computed (() => {
    const numSearch = arrayFavorite.value.find(num =>num ===counter.value)
    console.log(numSearch);
    if (numSearch === 0 ) return true
    return numSearch ? true : false ;
}) 

</script>

<template>
    <div class="container text-center mt-3">
        <h1>Hola mundo, esto es una prueba del {{ name1.toUpperCase()}} con fines de aprendizaje </h1>
    <div class="btn-group">
        <button @click="increment" class="btn btn-success">Aumentar</button>
        <button @click="decrement" class="btn btn-danger">Disminuir</button>
        <button @click="reset" class="btn btn-success">Reset</button>
        <button @click="add" :disabled="bloquearBtnAdd" class="btn btn-primary">Add</button>
    </div>
        <h2 :class="classCounter">{{ counter }}</h2>
    <ul class="list-group mt-3">
        <li class="list-group-item" v-for="(num, index) in arrayFavorite" :key="index">
            {{ num }}
        </li>
    </ul>    
    </div>
</template>

<style>
h1{
    color: rgb(155, 6, 224) 
  } 

.positive {
    color: green;
}  

.negative {
    color:red
}

.zero{
    color:white
}
</style>
