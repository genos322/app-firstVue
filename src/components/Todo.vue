<template>
  <v-container class="pt-12">
    <v-row class="justify-center">
      <v-col cols="12" sm="6" md="8">
        <v-row class="mx-4">
          <v-text-field
            v-model="task"
            counter="120"
            requiered
            label="Tareas"
            color="deep-purple lighten-4"
            placeholder="Ingrese una tarea"
          ></v-text-field>
          <v-btn class="ml-6" fab dark small color="purple" @click="saveTask()">
            <v-icon dark>{{ editIcon }}</v-icon>
          </v-btn>
        </v-row>
      </v-col>
    </v-row>
    <v-card class="mx-auto mt-16" max-width="600">
      <v-list>
        <v-list-item-group v-model="selectedIndex" mandatory color="purple lighten-3">
          <v-list-item v-for="(item, i) in tasks" :key="i">
            <v-list-item-icon class="d-none d-sm-flex">
              <v-icon>mdi-calendar-clock</v-icon>
            </v-list-item-icon>

            <v-list-item-content>
              <v-list-item-title v-text="item.text"></v-list-item-title>
            </v-list-item-content>
            <v-list-item-action class="d-flex flex-row align-center">
              <v-checkbox
                v-model="item.status"
                color="deep-purple accent-4"
              ></v-checkbox>
              <v-btn icon color="purple" class="ml-2" @click="editTask(item.text)">
                <v-icon>mdi-pencil</v-icon>
              </v-btn>
              <v-btn icon color="purple" @click="deleteTask(item)">
                <v-icon>mdi-delete</v-icon>
              </v-btn>
            </v-list-item-action>
          </v-list-item>
        </v-list-item-group>
      </v-list>
    </v-card>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      task: "",
      isEditing: false,
      tasks: [
        {
          text: "Preparar mi desayuno",
          status: false,
        },
        {
          text: "Agendar reunones",
          status: false,
        },
        {
          text: "Pedir el almuerzo",
          status: false,
        },
      ],
      selectedIndex: -1,
    };
  },
  methods: {
    editTask(item) {
      this.isEditing = true;
      this.task = item
    },
    
    saveTask() {
      console.log('in save');
      if (this.isEditing) {
        // Editar el elemento 
        const taskEdited = {
          text: this.task,
          status: false,
        }
        Object.assign(this.tasks[this.selectedIndex], taskEdited)
      } else {
        // Agregar el elemento al Arr
        this.tasks.push({
          text: this.task,
          status: false,
        })
      }
      this.task = ''
      this.isEditing = false
    },

    deleteTask() {
      console.log('in delete');
      this.tasks.splice(this.selectedIndex, 1)
    }
  },
  computed: {
    editIcon() {
     return this.isEditing ? 'mdi-content-save' : 'mdi-plus'
    }
  }
};
</script>

<style lang="scss" scoped></style>