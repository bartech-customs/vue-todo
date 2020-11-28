<template>
  <div class="grey--text text--lighten-2 pa-8 container">
    <v-form ref="form" @submit.prevent="addTask" dark class="mx-3">
      <v-container>
        <v-row class="align-center justify-center mx-auto ">
          <v-col cols="12" md="4">
            <v-text-field
              v-model="task"
              label="Task"
              outlined
              required
              :rules="rules.name"
              dark
              hide-details
              clearable
            ></v-text-field>
          </v-col>
          <v-col cols="12" md="4">
            <v-text-field
              v-model="task2"
              label="Description"
              outlined
              dark
              hide-details
              clearable
            ></v-text-field>
          </v-col>
          <v-btn type="submit">SUBMIT</v-btn>
        </v-row>
      </v-container>
    </v-form>
    <v-card class="mx-auto ma-2 ma-md-6 pa-md-15" elevation="4" dark>
      <v-list subheader two-line flat dark>
        <v-subheader>Tasks List </v-subheader>

        <v-list-item-group multiple>
          <v-list-item
            v-for="(task, index) in tasks"
            :key="index"
            @click="doneTask(index)"
          >
            <template v-slot:default>
              <v-list-item-action>
                <v-checkbox
                  :input-value="task.isComplete"
                  color="primary"
                ></v-checkbox>
              </v-list-item-action>

              <v-list-item-content :class="{ 'grey--text': task.isComplete }">
                <v-list-item-title>{{ task.title }}</v-list-item-title>
                <v-list-item-subtitle>{{ task.title2 }}</v-list-item-subtitle>
              </v-list-item-content>
              <v-list-item-action>
                <v-btn elevation="1" icon @click.stop="deleteTask(index)">
                  <v-icon color="grey lighten-1">mdi-delete</v-icon>
                </v-btn>
              </v-list-item-action>
            </template>
          </v-list-item>
        </v-list-item-group>
      </v-list>
    </v-card>
  </div>
</template>

<script>
export default {
  data() {
    return {
      task: null,
      task2: null,
      feedback: null,
      tasks: [
        {
          id: 1,
          title: "code along",
          title2: "vue js is the best",
          isComplete: false,
        },
        {
          id: 2,
          title: "buy sweetens",
          title2: "cake, chocolate",
          isComplete: true,
        },
        {
          id: 3,
          title: "do some excersise",
          title2: "dumbbell hammer curls",
          isComplete: false,
        },
      ],
      rules: {
        name: [(val) => (val || "").length > 0 || "This field is required"],
      },
    };
  },
  methods: {
    doneTask(id) {
      return (this.tasks[id].isComplete = !this.tasks[id].isComplete);
    },
    deleteTask(id) {
      let deleteTask = this.tasks[id];
      this.tasks = this.tasks.filter((task) => task !== deleteTask);
    },
    addTask() {
      if (this.$refs.form.validate()) {
        let newTask = {
          id: new Date(),
          title: this.task,
          title2: this.task2,
          isComplete: false,
        };
        this.tasks.push(newTask);
        this.$refs.form.reset();
        this.$refs.form.resetValidation();
      }
    },
  },
};
</script>

<style lang="scss" scoped></style>
