<script setup>
import {onMounted, ref} from 'vue';
 
    const name = ref('Paulo');
    let status = ref('active');
    const tasks = ref(['task 1','task 2','task 3']);
    const newTask = ref('');

    let change = ()=>{
      if(status.value === 'active'){
        status.value = 'pending';
      }else if(status.value === 'pending'){
        status.value = 'inactive';
      }else{
        status.value = 'active';
      }
    };

    const addTask =()=>{
      if(newTask.value.trim() != ''){
        tasks.value.push(newTask.value);
        newTask.value = '';
      }
    };

    const deleteTask = (index) =>{
      tasks.value.splice(index, 1);
    }

    onMounted(async ()=>{
      try {
        const response = await fetch('https://jsonplaceholder.typicode.com/todos');
        const data = await response.json();
        tasks.value = data.map((task)=> task.title);
      } catch (error) {
        console.log('error fetching tasks');
      }
    });

</script>

<template>
  <h1>{{name}}</h1>
  <p v-if="status === 'active'">Use is active</p>
  <p v-else-if="status=== 'pending'">User is pending</p>
  <p v-else>User is inactive</p>

  <form @submit.prevent="addTask">
    <label for="newTask">Add New Task</label>
    <input type="text" id="newTask" name="newTask" v-model="newTask">
    <button type="submit">Submit</button>
  </form>
  
  <ul>
    tasks:
    <li v-for="(task, index) in tasks" :key="task">
      <span>{{ task }}</span>
      <button @click="deleteTask(index)">x</button>
    </li>
  </ul>
  <button @click="change">change status</button>
</template>

