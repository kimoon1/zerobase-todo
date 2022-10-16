<template>
  <div class="home">
    <h2>
      할 일 추가 앱
    </h2>
    <div>
      <input v-model="todo" type="text" placeholder="할 일을 적어주세요." />
      <button type="button" @click="addTodo">추가</button>
    </div>
    <ul>
      <li v-for="(item,idx) in todoList" :key="idx">
        <span>{{item}}</span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HomeView',
  data() {
    return{
      todo: '',
      todoList: [],
    };
  },
  methods: {
    addTodo() {
      this.todoList.push(this.todo)
      this.todo = '';
    }
  }

}
</script>

<style>
</style>