<template>
  <v-app>
    <v-app-bar app color="teal" dark class="d-flex justify-center">
      <div class="d-flex align-center">
        <!-- <h2>TODO APP</h2> -->
        <h2>INDECISION APP</h2>

      </div>
    </v-app-bar>

    <v-main>
      <!-- <Counter/> -->
      <!-- <Todo /> -->
      <Indecision></Indecision>
    </v-main>
  </v-app>
</template>

<script>
import Counter from "./components/Counter.vue";
import Todo from "./components/Todo";
import Indecision from "./components/Indecision.vue";

export default {
  name: "App",

  components: {
    Counter,
    Todo,
    Indecision
  },

  data: () => ({
    //
  }),
};
</script>