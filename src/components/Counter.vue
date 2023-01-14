<template>
    <div>
        <h2>hola, soy c</h2>
        <p>{{ contador}} <sup>2</sup> = {{ }}</p>
        <button @click="increase()">+1</button>
        <button @click="decrement()">-1</button>
    </div>
</template>

<script>    
export default {
    name: 'Counter',
    data() {
        return {
            contador: 10
        }
    },
    methods: {
        squareCounter() {
            this.contador = this.contador * this.contador;
        },
        increase(){
            this.contador++;
        },
        decrement(){
            this.contador--;
        }
    },
    computed: {
        squareComputer() {
            console.log('squareComputer');
            return this.contador * this.contador;
        }
    }
}
</script>
<style scoped>
    button {
        background-color: #4CAF50; /* Green */
        border: none;
        margin-left: 20px;
        color: white;
        padding: 15px 32px;
        text-align: center;
        text-decoration: none;
        display: inline-block;
        font-size: 16px;
        cursor: pointer;
        border-radius: 5px;
    }
</style> 