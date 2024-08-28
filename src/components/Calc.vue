<script setup>
import { reactive } from 'vue';

const aritmetica = reactive({
    num1: '',
    num2: '',
    calcs: {
        adicao: (a, b) => a + b,
        subtracao: (a, b) => a - b,
        divisao: (a, b) => a / b,
        multiplicacao: (a, b) => a * b
    },

    result: 0
})

const resultFinal = () => {
    const { num1, num2, operacoes } = aritmetica;
    aritmetica.result = aritmetica.calcs[operacoes](parseFloat(num1), parseFloat(num2))
}
</script>

<template>
    <div class="container">
        <form>
            <input type="number" v-model="aritmetica.num1" @input="resultFinal">
            <select v-model="aritmetica.operacoes" @change="resultFinal">
                <option value="adicao">+</option>
                <option value="subtracao">-</option>
                <option value="divisao">/</option>
                <option value="multiplicacao">*</option>
            </select>
            <input type="number" v-model="aritmetica.num2" @input="resultFinal"> =
            <span>{{ aritmetica.result }}</span>
        </form>
    </div>
</template>

<style scoped>
input {
    margin-right: 15px;
}

select {
    margin-right: 15px;
}

span {
    background-color: black;
    color: #fff;
    border-radius: 6px;
    padding: 5px;
    margin-right: 15px;
    margin-left: 15px;
}
</style>