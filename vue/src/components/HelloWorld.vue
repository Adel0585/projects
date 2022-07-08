<template>
  <div class="test-project">
    <div class="head"><h1>Todo List</h1></div>
    <!-- new task -->
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
                @click="addTask"
                :disabled="!tasktext"
              >
                create
              </v-btn>
            </v-col>
          </v-row>
        </v-container>
      </v-form>
    </div>

    <!-- delete All     -->

    <div class="delete-All">
      <v-btn block class="butn" v-if="tasks.length > 1" @click="deleteAll"
        >delete All tasks</v-btn
      >
    </div>
    <!-- tasks added -->
    <div>
      <div class="task-list" v-for="(task, index) in tasks" :key="index">
        <v-form>
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
        <div class="all-rections">
          <div class="My-icons">
            <div class="reaction">
              <v-icon color="blue darken-2" @click="likeReaction">
                mdi-thumb-up
              </v-icon>
            </div>
            <div class="reaction">
              <v-icon color="red darken-2" @click="dislikeReaction">
                mdi-thumb-down
              </v-icon>
            </div>
            <div class="reaction">
              <v-icon color="blue darken-0.5" @click="addComment"
                >mdi-message-text</v-icon
              >
            </div>
          </div>
          <div class="like-dislike">
            <div>
              <p>Like {{ like }}</p>
            </div>
            <div>
              <p>Dislike {{ dislike }}</p>
            </div>
          </div>
        </div>
        <!-- ----------------   -->
        <div class="comments" v-for="(comment, index) in comments" :key="index">
          <div class="comments-field">
            <v-container>
              <v-row>
                <v-col cols="12" md="12">
                  <v-textarea solo label="Comment..."></v-textarea>
                </v-col>
              </v-row>
            </v-container>
          </div>
          <!-- ----------------   -->
          <div class="del-comm">
            <v-icon
              color="red darken-2"
              @click="deleteComment(index)"
            >
              mdi-trash-can
            </v-icon>
          </div>
        </div>
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
    like: 0,
    dislike: 0,
    comments: [],
    comm: {},
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
    likeReaction: function () {
      this.like += 1;
    },
    dislikeReaction: function () {
      this.dislike += 1;
    },
    addComment: function () {
      this.comments.push({ comm: {}});
    },
    deleteComment: function (index) {
      this.comments.splice(index, 1);      
    },
  },
};
</script>

<style>
.test-project {
  background: #00ffff;
  height: 100%;
}
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
  margin-top: 0px;
  margin-bottom: 30px;
  font-size: 1.9rem;
  color: #0000cd;
}
.head h1 {
  padding-top: 20px;
}
.task-list {
  margin-bottom: 0;
  padding-left: 5px;
}
.all-rections {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-left: -50px;
  margin-top: -20px;
  width: 80%;
}
.My-icons {
  display: flex;
  align-items: center;
  margin-left: 60px;
  width: 15%;
  padding: 0 10px;
  justify-content: space-between;
}
.My-icons h3 {
  cursor: pointer;
  color: black;
}
.reaction {
  cursor: pointer;
  transition: 0.4s;
}
.like-dislike {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 150px;
}
.comments {
  display: flex;
}
.comments-field {
  width: 600px;
}
</style>
