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
            <h1>{{question}}</h1>
            <h2>Si, No... Quiza</h2>
  
            <div class="pt-8">
              <v-img
          src="https://cdn.vuetifyjs.com/images/parallax/material2.jpg"
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
      isValidQuestion: false,
    }
    },
    watch: {
      question(value, oldValue) {
        console.log('new value', value);
        console.log('old value', oldValue);
        if (!value.includes("?")) return;
        this.isValidQuestion = true;
        //TODO: Realizar la peticion de la API: https://yesno.wtf/api
      }
  }
  };
  </script>
  
  <style lang="scss" scoped></style>