<template>
    <div>
        <div class="d-flex flex-column align-center pt-10">
            <h2>hola, soy c</h2>
            <p>{{ contador }} <sup>2</sup> = {{ squareComputer }}</p>
            <div>
                <v-btn class="mx-2" fab dark small color="primary" @click="decrement">
                <v-icon dark> mdi-minus </v-icon>
            </v-btn>
            <v-btn class="mx-2" fab dark small color="purple" @click="increase">
                <v-icon dark> mdi-plus </v-icon>
            </v-btn>

            </div>
        </div>
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
        increase() {
            this.contador++;
        },
        decrement() {
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
    
</style> 