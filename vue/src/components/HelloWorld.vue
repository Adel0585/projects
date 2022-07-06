<template>
  <div>
    <div class="head"><h1>Todo List</h1></div>
    <div class="new-tasks">
      <v-form>
        <v-container>
          <v-row>
            <v-col cols="11" class="input">
              <v-text-field
                class="input"
                v-model="tasktext"
                id="new-task"
                label="New Task"
                solo
                dense
              ></v-text-field>
              <v-btn
                class="btn"
                depressed
                color="primary"
                @click.prevent="addTask"
                :disabled="!tasktext"
              >
                create
              </v-btn>
            </v-col>
          </v-row>
        </v-container>
      </v-form>

      <div class="delete-All">
        <v-btn block class="butn" v-if="tasks.length > 1" @click="deleteAll"
          >delete All tasks</v-btn
        >
      </div>
      <div class="task-list">
        <v-form v-for="(task, index) in tasks" :key="index">
          <v-container>
            <v-row>
              <v-col cols="11" class="input">
                <v-text-field
                  v-model="task.Text"
                  readonly
                  @click="task.done = !task.done"
                  :style="{
                    'text-decoration': task.done ? 'line-through' : '',
                  }"
                >
                </v-text-field>

                <v-btn
                  class="btn"
                  depressed
                  color="primary"
                  @click="deleteTask(index)"
                >
                  delete
                </v-btn>
              </v-col>
            </v-row>
          </v-container>
        </v-form>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    tasks: [],
    tasktext: "",
    done: true,
  }),
  methods: {
    addTask: function () {
      this.tasks.push({ Text: this.tasktext, done: false });
      this.tasktext = "";
    },
    deleteTask: function (index) {
      this.tasks.splice(index, 1);
    },
    deleteAll: function () {
      this.tasks = [];
    },
  },
};
</script>
<style>
.input {
  display: flex;
  align-content: center;
  justify-content: space-between;
}
.btn {
  margin-left: 20px;
}
.delete-All {
  margin: 20px 320px;
}
.head {
  text-align: center;
  margin-top: 50px;
  margin-bottom: 30px;
  font-size: 1.5rem;
  color: aqua;
}
</style>
