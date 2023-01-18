<template>
    <v-container>
      <v-row class="justify-center">
        <v-col cols="12" sm="6" md="8">
          <v-text-field
            v-model="question"
            label="Pregunta"
            placeholder="Hazme una pregunta"
          ></v-text-field>
          <p>Recuerda terminar con un signo de interrogación (?)</p>
          <div>
            <h1>{{ question }}</h1>
            <h2>{{answer}}</h2>
  
            <div class="pt-8">
              <v-img
                :src="image"
                gradient="to top right, rgba(100,115,201,.33), rgba(25,32,72,.7)"
              ></v-img>
            </div>
          </div>
        </v-col>
      </v-row>
    </v-container>
  </template>
  
  <script>
  export default {
    data() {
      return {
        question: "",
        answer: null,
        isValidQuestion: false,
        image: null
      };
    },
    // created () {
    //   this.promesa(false);
    // },
    watch: {
      question(value, oldValue) {
        if (!value.includes("?")) return;
        this.isValidQuestion = true;
        //TODO: Realizar la peticion de la API: https://yesno.wtf/api
        this.getAnswer();
      },
    },
    methods: {
  
      promesa(param) {
        console.log('Inicio')
        new Promise((resolve, reject) => {
          console.log('Cuerpo de la promesa')
          param ? resolve('La promsa se resolvio correctamente') : reject('La promesa fue rechazada')
        }).then(console.log).catch(console.log)
        console.log('Fin')
      },
  
      async getAnswer() {
        console.log('in get answer')
        this.answer = 'Pensando...'
        const {answer, image} = await fetch("https://yesno.wtf/api").then((r) => r.json())
        this.answer = answer === 'yes' ? 'Si' : 'No'
        this.image = image
      }
    },
  };
  </script>
  
  <style lang="scss" scoped></style>