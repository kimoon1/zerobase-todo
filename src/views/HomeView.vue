<template>
  <div class="home">
    <div class="container">
      <h2 class="title">
        할 일 추가 앱
      </h2>
      <div class="add-area">
        <input class="add-input" v-model="todo" type="text" placeholder="할 일을 적어주세요." />
        <button class="add-button" type="button" @click="addTodo">추가</button>
      </div>
      <ul class="todo-list">
        <li class="todo-item" v-for="(newTodo,idx) in todoList" :key="idx">
          <div class="todo-area">
            <input type="checkbox" v-model="newTodo.isChecked" />
            <span v-if="!newTodo.isUpdate" @click="newTodo.isUpdate = true"
              :class="{isFinish: newTodo.isChecked}">{{newTodo.name}}</span>
            <span v-else>
              <input v-model="newTodo.name" type="text" placeholder="할 일을 적어주세요.">
              <button type="button" @click="newTodo.isUpdate = false">수정 완료</button>
            </span>
          </div>
          <div class="button-area">
            <button @click="deleteTodo(idx)">삭제</button>
          </div>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HomeView',
  data() {
    return{
      todo: '',
      todoList: [
        {
          name: '농구',
          isUpdate: false,
          isChecked: false,
        },{
          name: '축구',
          isUpdate: false,
          isChecked: false,
        },
        {
          name: '배구',
          isUpdate: false,
          isChecked: false,
        }

      ],
    };
  },
  methods: {
    addTodo() {
      const newTodo = {
        name: this.todo,
        isUpdate: false,
        isChecked: false,
      };
      this.todoList.push(newTodo)
      this.todo = '';
    },
    deleteTodo(idx) {
      this.todoList = this.todoList.filter((item, index) => index !== idx)
    },
  }

}
</script>

<style>
.home {
  width: 100%;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
}

.container {
  width: 500px;
  height: 500px;
  border: 1px solid black;
  padding: 24px;
}

.title {
  text-align: center;
}

.add-area {
  display: flex;
  align-items: center;
  justify-content: end;
}

.add-input {
  width: 150px;
  height: 40px;
  outline: none;
  border: 1px solid rgba(0, 0, 0, .15);
  padding-left: 8px;
  margin-right: 8px;
}

.add-input:hover {
  border-color: rgba(0, 0, 0, .54);
}

.add-input:focus {
  border-color: #00c4c4;
}

.add-button {
  width: 80px;
  height: 40px;
  background-color: #00c4c4;
  color: #fff;
  border: 1px solid #00c4c4;
  cursor: pointer;
  margin: 16px 0;
}

.add-button:hover {
  border-color: #00b2b2;
  background-color: #00b2b2;
}

.todo-list {
  width: 100%;
}

.todo-item {
  width: 100%;
  height: 30px;
  border-bottom: 1px solid gray;
  padding: 8px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.isFinish {
  text-decoration: line-through;
}
</style>