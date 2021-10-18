<template>
    <div id="app">
        <h1 style="color: black">Problema de monty hall</h1>
        <div class="form">
            <div v-if="!started">
                <label class="questions" for="portsAmount">Quantas Portas?</label>
                <input type="text" id="portsAmount" size="3"
                    v-model.number="portsAmount">
            </div>
            <div v-if="!started">
                <label class="questions" for="selectedPort">Porta premiada</label>
                <input type="text" id="selectedPort" size="3"
                    v-model.number="selectedPort">
            </div>
            <button v-if="!started" @click="started=true">Iniciar</button>
            <button v-if="started" @click="started=false">Reiniciar</button>
        </div>
        <div class="doors" v-if="started">
            <div v-for="i in portsAmount" :key="i">
                <Door :number="i"
                :hasGift="i == selectedPort"/>
            </div>
        </div>
    </div>
</template>

<script>
import Door from '@/components/Door.vue'

export default {
    name: 'App',
    components: {
        Door
    },
    data() {
        return {    
            started: false,
            portsAmount: 3,
            selectedPort: null
        }
    }
}
</script>

<style>
    * {
        box-sizing: content-box;

    }
    body {
        color: #fff;
        background: linear-gradient(0.25turn, #3f87a6, #ebf8e1, #f69d3c);
    }
    #app {
        display: flex;
        flex-direction: column;
        align-items: center;
    }
    #app h1 {
        border: 1px solid #000;
        background-color: #0004;
        padding: 20px;
        margin-bottom: 60px;
    }
    .form {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        margin-bottom: 40px;
    }

    .form, .form input, .form button {
        margin-bottom:10px;
        font-size:2rem;
    }
    .questions {
        border: 1px solid #000;
        background-color: #0004;
        padding: 10x;
        margin-bottom: 10px;
        margin-right: 10px;
    }
    .doors {
        align-self: stretch;
        display: flex;
        justify-content: space-around;

        flex-wrap: wrap;
    }
</style>