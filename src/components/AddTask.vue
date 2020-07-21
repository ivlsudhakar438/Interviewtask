<template>
  <section class="interview-add-task-form">
    <h3 class="task-heading">Add Task</h3>
    <div class="vue-add-form">
      <el-form v-model="addTaskForm" :rules="rules" ref="addTaskForm">
        <el-row :gutter="10">
          <el-col :span="12">
            <el-form-item label="Task Title" prop="title" required>
              <el-input type="text" v-model="addTaskForm.title"></el-input>
            </el-form-item>
          </el-col>
        </el-row>
        <el-row :gutter="10">
          <el-col :span="12">
            <el-form-item label="Description" prop="description" required>
              <el-input
                type="textarea"
                autosize
                placeholder="Please input"
                v-model="addTaskForm.description"
                required="true"
              ></el-input>
            </el-form-item>
          </el-col>
        </el-row>
        <el-row>
          <el-button type="primary" @click="addToTasks">Submit</el-button>
        </el-row>
      </el-form>
      <hr />
    </div>
    <div class="tasks-lists" v-if="totalTasks && totalTasks.length">
      <el-row :gutter="30">
        <el-col :span="12" v-for="(item, index) in totalTasks" :key="index">
          <div class="single-task">
            <div slot="header" class="clearfix">
              <span>{{ item.title + "  " + item.description }}</span>
              <el-button
                style="float: right; padding: 3px 0"
                type="text"
                @click="closeCheckList(index)"
              >
                X
              </el-button>
              <el-button
                style="float: right; padding: 3px 0"
                type="text"
                @click="addCheckList(index)"
              >
                +
              </el-button>
            </div>
          </div>
        </el-col>
      </el-row>
    </div>
  </section>
</template>

<script>
export default {
  name: "AddTask",
  data() {
    return {
      addTaskForm: {
        title: "",
        description: "",
      },
      rules: {
        title: [
          { required: true, message: "Please Add Title", trigger: "blur" },
          { min: 3, message: "Min Length should be 3", trigger: "blur" },
        ],
        description: [
          {
            required: true,
            message: "Please Add Description",
            trigger: "blur",
          },
        ],
      },
      totalTasks: [],
    };
  },
  methods: {
    addToTasks() {
      let params = {
        title: this.addTaskForm.title,
        description: this.addTaskForm.description,
      };
      this.totalTasks.push(params);
      this.addTaskForm.title = "";
      this.addTaskForm.description = "";
    },
    addCheckList(index) {
      console.log(index);
    },
    closeCheckList(index) {
      console.log(index);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.interview-add-task-form .task-heading {
  margin: 20px;
  color: #80f880;
  font-size: 2em;
  font-weight: 600;
}
.interview-add-task-form .vue-add-form {
  width: 100%;
  font-size: 1em;
  color: #242121;
  margin: 1.5em;
}
.interview-add-task-form .vue-add-form input {
  width: 95%;
  margin: 20px;
}
.interview-add-task-form .vue-add-form .required-field {
  color: #ff4444;
  font-size: 0.75em;
  margin-left: 1px;
}
</style>
