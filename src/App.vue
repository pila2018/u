<template>
<h4>Today's tasks</h4>



<div class="tasks">
  <div
   class="task"
   :class="{completed: task.isCompleted}" 
   v-for="task in tasks" 
   :key="task._id"
  @click="completedHandler(task._id)"
   >


  <div class="round"
  :class="{ 
  business: task.type == 'business',
  personal: task.type == 'personal',}"></div>
    
  <span> {{task.name}}</span>
   
   <div class="remove-task-icon" @click="removeTask(task._id)">
     <img src="./assets/trash.png" alt="">
   </div>
</div>
</div>
<div class="add-task">
  <input type="text" placeholder="Название задачи" v-model="taskName"
   v-on:keyup.enter="addTask" />
<button @click="addTask">+</button>
</div>

</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'
//<div class="wrapper-stat">
  //<div class="sat">
    //<div class="h5">Business</div>
    //<div class="wrapper-progress">
      //<div class="bar"></div>
    //</div>
  //</div>
  //<div class="sat personal">
   // <div class="h5">Personal</div>
   // <div class="wrapper-progress">
     // <div class="bar"></div>
    //</div>
  //</div>
//</div>
export default {
  name: 'App',
  data(){
    return{
      taskName:'',
     tasks: [
       {
       _id:'asdasd1234',
       name:'Create to do app in vue js',
       isCompleted: false,
       type:'business',
     },
     ],
    };
  },
  methods: {
     completedHandler: function(taskId) 
    {
     const currentTask = this.tasks.find((t) => t._id == taskId);
     currentTask.isCompleted = !currentTask.isCompleted;
    },
    addTask: function(){
      this.tasks.push({
        _id: Math.random().toString(36).substring(2,7),
       name: this.taskName,
        isCompleted: false,
       type:'personal',
        });
        this.taskName = ''
    },


    removeTask: function(taskId)
    {
     this.tasks=this.tasks.filter(t => t._id != taskId);
    }
  },
};
</script>

<style>

</style>
