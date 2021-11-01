<template>
<div class="container">
  <div id="app">
    <h1 class="text-center mt-5">To Do List Vue!</h1>
    <main class="mainContainer">
        <input type="text" class="form-control w-50 me-3" @keyup.enter="add()" v-model="newToDo">
            <button class="btn btn-primary" @click="add()">Add</button>
    </main>
	<div class="list">
    <ul style="list-style: none" class="list">
      <li class="listItem mt-3" v-for="(todo,i) in existingToDo" :key="todo.id">
        <h3>
          {{i+1}}: {{todo.text}}
        </h3>
        <button class="btn btn-danger ms-3" @click="deleteToDo(i)">X</button>
      </li>
    </ul>
	</div>

  </div>
</div>
</template>

<script>
export default {
  name: 'App',
 data(){
   return{
     newToDo:'',
     existingToDo:[
       {text: 'To Do List Vue',id: 0},
       {text: 'Do Groceries',id: 1},
       {text: 'Walk dog',id: 2},
     ],
     
   }
 },
 methods:{
       add(){
         this.existingToDo.push({
           text:this.newToDo,
           id: new Date().valueOf()
         }),
         this.newToDo = ''
       },
       deleteToDo(i){
         this.existingToDo.splice(i,1)
       }
     }
}
</script>

<style>
body{
height:50%;
}
.container{
	background: #41B883;
	border-radius: 10px;
	padding:10px;
	margin-top: 50px;
}
.mainContainer{
  display: flex;
  flex-wrap:nowrap;
  justify-content: center;
}

.list{
	display: flex;
	flex-direction: column;
	align-items: center;
}

.listItem{
	display: flex;
}
</style>
