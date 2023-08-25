<script setup>
import { reactive } from 'vue';

    const estado = reactive({
        numero: 0,
        numero1: 0,
        resultado:0,
        operacao: '',
    })

    const adicao = () =>{
        const { numero, numero1 } = estado;
        return numero + numero1;
        
    }
    const multiplicacao = () =>{
        const { numero, numero1 } = estado;
        return numero * numero1;
    }
    const divisao = () =>{
        const { numero, numero1 } = estado;
        if(numero1 === 0){
            return
        }
        return numero / numero1;
    }
    const subtracao = () =>{
        const { numero, numero1 } = estado;
        return numero - numero1;
    }

    const getOperacao = () => {
        const { operacao } = estado;
        
        switch(operacao){
            case 'adicao':
                return adicao();
            case 'multiplicacao':
                return multiplicacao();
            case 'divisao':
                return divisao();
            case 'subtracao':
                return subtracao();
        }
    }
</script>

<template>
  <div class="container">
    <header class="p-5 mb-4 bg-light rounded-3">
        <h1 class="">Calculadora VUE JS</h1>
    </header>
    <form @submit="capturarNumero">
        <div class="row">
            <div class="col-md-4">
                <input @change="evento => estado.numero = +evento.target.value" required type="number" class="form-control" placeholder="Digite o primeiro numero">
            </div>
            <div class="col-md-4">
                <input @change="evento => estado.numero1 = +evento.target.value" required type="number" class="form-control" placeholder="Digite o segundo numero">
            </div>
            <div class="col-md-4">
                <select @change="evento=> estado.operacao = evento.target.value" class="form-control">
                    <option value="adicao">Adição</option>
                    <option value="multiplicacao">Multiplicação</option>
                    <option value="divisao">Divisão</option>
                    <option value="subtracao">Subtração</option>
                </select>
            </div>
        </div>
    </form>
    
    <span class="fs-1">Resultado: {{ estado.resultado = getOperacao() }}</span>
  </div>
</template>

<style scoped>
    
</style>
