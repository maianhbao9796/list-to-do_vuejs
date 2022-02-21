<template>
  <div class="interact-screen">
    <h1 class="interact-screen__title">DANH MỤC CÔNG VIỆC CẦN LÀM</h1>
    <div class="interact-screen__input">
      <AddTodoComponent @on-add-todo="onHandleAddTodo" />
    </div>
    <div class="interact-screen__list">
      <ItemTodoComponent
        v-for="todo in todos"
        :key="todo.id"
        :todo="todo"
        @on-check-todo="onCheckTodoHandle"
        @on-delete-todo="onDeleteTodoHandle"
        @on-update-todo="onUpdateTodoHandle"
      />
    </div>
  </div>
</template>

<script>
import AddTodoComponent from '@/components/AddTodoComponent.vue';
import ItemTodoComponent from '@/components/ItemTodoComponent.vue';
import axios from 'axios';

export default {
  name: 'InteractScreen',
  components: {
    AddTodoComponent,
    ItemTodoComponent,
  },
  data() {
    return {
      isCompleted: true,
      todos: [],
    };
  },
  created() {
    // axios
    //   .get(`https://jsonplaceholder.typicode.com/todos`)
    //   .then((response) => {
    //     this.todos = response.data;
    //     console.log(response);
    //   })
    //   .catch((e) => {
    //     this.errors.push(e)
    //     console.log(e);
    //   });
    const getAllTodos = async () => {
      try {
        const res = await axios.get(
          'https://jsonplaceholder.typicode.com/todos'
        );
        console.log(res);
      } catch (error) {
        console.log(error);
      }
    };

    getAllTodos;
  },

  mounted() {

    const myPromise = new Promise((resolve) => {
      setTimeout(() => {
        resolve();
      }, 300);
    })
    const callAPI = axios('URL');

    myPromise.then(() => {
      console.log('Line 1');
    })
    console.log('Line 2');
    callAPI.then((response) => {
      console.log(response);
    })
    console.log('Line 3');

  },

  methods: {
    onHandleAddTodo(titleInput) {
      console.log(this.todos.length);
      console.log('Với nội dung là: ' + titleInput);

      if (titleInput == '') {
        alert('Vui lòng điền thông tin');
      } else {
        this.todos.push({
          id: this.todos.length + 1,
          title: titleInput,
          ompleted: false,
        });
      }

      // const newObject = {
      //     id: this.todos.length + 1,
      //     title: titleInput,
      //     ompleted: false,
      // };
      // this.todos.push(newObject);
      // console.log('Đã thêm đối tượng:', newObject);
    },
    onCheckTodoHandle(item) {
      // console.log(item);
      item.completed = !item.completed;
    },
    onDeleteTodoHandle(item) {
      const index = this.todos.findIndex((todo) => todo.id === item.id);
      console.log('Đã xóa thứ tự số:' + index);
      this.todos.splice(index, 1);
    },
    onUpdateTodoHandle(item, titleEdited) {
      const itemSelect = this.todos.find((todo) => todo.id === item.id);
      console.log(itemSelect);
      itemSelect.title = titleEdited;
    },
  },
};
</script>

<style lang="scss" scoped>
.interact-screen {
  display: flex;
  flex-direction: column;
  align-items: center;

  &__title {
    color: #ffffff;
    margin-top: 60px;
    text-shadow: 1px 1px 10px rgb(0, 0, 0, 0.9);
    cursor: default;
  }
  &__input {
    width: 50%;
  }
  &__list {
    background-color: #ffffff;
    height: 300px;
    width: 50%;
    margin: 30px;
    border-radius: 5px;
    border: none;
    overflow-y: scroll;
    scroll-behavior: smooth;
    scrollbar-width: none;
    box-shadow: 0 0 10px 2px rgb(0 0 0 / 20%);
  }
}
</style>
