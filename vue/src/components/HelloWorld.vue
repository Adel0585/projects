<template>
  <div>
    hello
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
              >
                create
              </v-btn>
            </v-col>
          </v-row>
        </v-container>
      </v-form>
    
    <div class="delete-All">
      <v-btn block class="butn">delete All tasks</v-btn>
    </div>
<div class="task-list">
      
      <v-form v-for="(task, index) in tasks" :key="index">
        <h1>{{task}}</h1>
        <v-container>
          <v-row>
            <v-col cols="12" class="input">
              <v-text-field v-model="task.tasktext" >
              
              </v-text-field>
             

              <v-btn class="btn" depressed color="primary"> update </v-btn>
              <v-btn class="btn" depressed color="primary"> delete </v-btn>
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
    tasktext:'',
  }),
  methods: {
    addTask: function () {
      this.tasks.push({ Text:this.tasktext, done: false });
      this.tasktext = "";
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
</style>
