<template>
  <div class="todolist">
    <form @submit.prevent class="todo-header">
        <h1 class="title">Список задач</h1>
        <input 
               :value="task"
               @input="valueTask"
               class="todo-inputtype" 
               type="text" 
               placeholder="Укажите задачу"
        />
        <button @click="createTask" class="btn">+</button>
    </form>    
        <div class="todo-main">
            <ul class="todo-list">
                <li v-bind:key="t" v-for="t in listTask" class="todo-item">
                 {{ t.task }}
                   <a 
                     :id=" t.id "
                     @click.prevent
                     @click="delitTask"
                     href="#"
                    class="todo-list__delit"
                 >удалить
                   </a>   
                </li>
            </ul>
        </div>  
    </div>
</template>

<script>
  
    export default {
      data() {
        return {
          listTask: [
            { id: 1, task: "Выполнить дизайн" },
            { id: 2, task: "Сделать вёрстку сайта" },
            { id: 3, task: "Загрузить в репозиторий" },
          ],
          task: "",
          data: 0,
        };
      },
      methods: {
        valueTask() {
          console.log(this.task.value);
        },
        createTask() {
          const newTask = {
                id: Date.now(),
                task: this.task,
            };
            console.log(newTask);
            this.listTask.push(newTask);
            this.task = "";
        },
      },
    };
</script>
<style scope>
 *{ 
   margin: 0;
   padding: 0;
   box-sizing: border-box;
  }
body {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  background: linear-gradient(#a820a8,#0a1ed0);
  background-repeat: no-repeat;
}
#app {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 75px;
  margin-bottom: 100px;
}
.title {
  margin-top: 20px;
  font-size: 32px;
  text-align: center;
  margin-bottom: 30px;
}
.todo-inputtype {
  padding: 10px 20px;
  border: 1px solid #ccc;
  border-radius: 20px;
  width: 300px;
}
.btn {
  font-size: 40px;
  padding: 10px;
  border-radius: 50%;
  background-color: red;
}
.todo-main {
  margin-top: 30px;
}
.todo-list {
   list-style: none;
   margin: 0;
   padding: 0;
   font-size: 0;
}
.todo-item {
  font-size: 20px;
  color:black;
  padding: 5px 10px;
  background-color: #fff;
  margin-top: 5px;
  margin-bottom: 5px;
  border-radius: 10px;
}
</style>





