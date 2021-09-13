<template>
  <div class="Todo">
    <h1 style="font-family:Courier New;">Todo App</h1><br>
    <input type="text" class="form-control" placeholder="Enter Task..." v-model="task">
    <button class="btn btn-primary" type="submit" value="Submit" @click="newTask">Submit</button>
    <table class="table table-bordered">
      <thead class="up">
      <tr>
        <th scope="col" width="490px;">Task</th>
        <th scope="col" width="110px;">Status</th>
        <th scope="col" width="98px">#</th>
        <th scope="col" width="185px;">#</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="(task, index) in tasks" :key="index">
        <th class="taskname">{{ task.name }}</th>
        <td class="taskstatus">{{ donetxt }}</td>
        <td>
          <button type="button" class="btn btn-danger" @click="delTask">Delete</button>
        </td>
        <td>
          <button type="button" class="btn btn-success" @click="done">Change
          Status</button>
        </td>
      </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: 'Todo',
  task: '',
  data() {
    return {
      donetxt: 'Undone',
      tasks: [
      ],
    };
  },
  methods: {
    newTask() {
      if (this.task === '') {
        console.log('Task Cant Be Empty!');
      } else {
        this.tasks.push({
          name: this.task,
          status: 'Undone',
        });
      }
    },
    delTask(index) {
      this.tasks.pop(index, 1);
    },
    done() {
      if (this.donetxt === 'Undone') {
        this.donetxt = 'Done';
      } else {
        this.donetxt = 'Undone';
      }
    },
  },
};
</script>
<style scoped>
.bi-trash {
  width:50px;
  height:50px;
}
.form-control {
  position: relative;
  left:535px;
  width:490px;
}
.btn-primary {
  position: relative;
  left:296px;
  top:-38px;
}
.table-bordered {
  position:relative;
  left:360px;
  width:890px;
}
.taskname {
  position: relative;
  top:6px;
}
.taskstatus {
  position: relative;
  top:6px;
}
</style>
