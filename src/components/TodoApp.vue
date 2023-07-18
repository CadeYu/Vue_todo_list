<template>
<div class="container">
  <p class="text-center">Vue-todolist</p>

  <!-- 输入框 -->
<div class="d-flex">
  <input v-model="task"  type="text" class="form-control" placeholder="输入任务" aria-label="task's username" aria-describedby="basic-addon2">
  <button type="button" class="btn btn-dark" @click="submit">提交</button>
</div>

<!-- 表单 -->
<table class="table table-bordered border-primary table-striped mt-5">
  <thead>
    <tr >
      <th scope="col">任务</th>
      <th scope="col">状态</th>
      <th scope="col" class="text-center">#</th>
      <th scope="col" class="text-center">#</th>
    </tr>
  </thead>
  <tbody >
    <tr v-for="(task,index) in tasks" :key="index">
      <th scope="row">{{task.name }}</th>
      <td>{{task.status}}</td>
      <td> 
        <div class="text-center" @click="changeStatus(index)">
          <p class="fa fa-pen">11</p>
        </div>
      </td>
      <td>
        <div class="text-center" @click="deleteTask(index)">
          <p class="fa fa-trash" ></p>
        </div>
      </td>
    </tr>
  </tbody>
</table>

</div>
</template>

<script>
export default {
  name: 'TodoApp',
  props: {
    msg: String
  },
  // 定义响应式数据

  data () {
    return {
      // 让提交按钮绑定双向数据，这样我们可以拿到框框中的值
      task: '',
      

      tasks: [
        {
          name : '洗澡',
          status : '已完成'
        },
        {
          name : '做作业',
          status : '未完成'
        }
      ],
      flag: false
    }
  },
  methods: {
    submit () {
      //特殊情况检查
      if(this.task.length == 0){
        return
      }else{
        this.tasks.push({
          name: this.task,
          status: '未完成'
        })
      }
      
    },

    deleteTask(index){
      this.tasks.splice(index,1)
    },
    changeStatus(index){
        this.flag = !this.flag
        if(this.flag){
          this.tasks[index].status = '未完成'
        }else{
        this.tasks[index].status = '已完成'
      }
   }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
