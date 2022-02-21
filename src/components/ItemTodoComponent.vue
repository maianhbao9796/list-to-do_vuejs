<template>
  <div class="item-to-do-component">
    <div class="item-to-do-component__content">
      <input
        type="checkbox"
        v-if="!isEdit"
        :checked="todo.completed"
        @change="onCheckTodo"
        class="item-to-do-component__content__check"
      />
      <span
        v-if="!isEdit"
        class="item-to-do-component__content__label"
        :class="todo.completed ? 'is-completed' : ''"
      >
        {{ todo.title }}</span
      >
      <input
        type="text"
        v-else
        class="item-to-do-component__content__input"
        v-model="titleEdit"
        @keypress.enter="onUpdateTodo"
      />
    </div>
    <div class="item-to-do-component__btn">
      <button
        v-if="!isEdit"
        class="item-to-do-component__btn__edit"
        @click="onEditTodo"
      >
        Sửa
      </button>
      <button
        v-if="!isEdit"
        class="item-to-do-component__btn__del"
        @click="onDeleteTodo"
      >
        Xóa
      </button>
      <button
        v-else
        class="item-to-do-component__btn__update"
        @click="onUpdateTodo"
      >
        Cập nhật
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ItemTodoComponent',
  props: {
    todo: {},
  },
  data() {
    return {
      titleEdit: '',
      isEdit: false,
    };
  },
  mounted() {
    console.log(this.titleEdit);
    this.titleEdit = this.todo.title;
    console.log(this.titleEdit);
  },
  methods: {
    onCheckTodo() {
      this.$emit('on-check-todo', this.todo);
    },
    onDeleteTodo() {
      this.$emit('on-delete-todo', this.todo);
    },
    onEditTodo() {
      console.log(this.titleEdit);

      this.isEdit = true;
    },
    onUpdateTodo() {
      this.$emit('on-update-todo', this.todo, this.titleEdit);
      this.isEdit = false;
    },
  },
};
</script>

<style lang="scss" scoped>
.filter-todo {
  filter: brightness(0.5);
}
.item-to-do-component {
  background: #f1f1f1;
  margin: 5px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  &__content {
    flex: 1;
    padding: 5px 0;
    display: flex;
    align-items: center;
    justify-content: flex-start;
    margin-right: 40px;
    overflow: hidden;
    &__check {
      margin: 0 10px;
    }
    &__label {
      color: #068bc0;
      text-align: left;
      font-size: 14px;
      line-height: 16px;
      word-wrap: break-word;
      &.is-completed {
        text-decoration: line-through;
      }
    }
    &__input {
      flex: 1;
      margin-left: 23px;
      border: none;
      padding: 3px;
    }
  }
  &__btn {
    &__edit {
      background-color: #f9a60b;
      color: #ffffff;
      border: none;
      width: 60px;
      padding: 5px;
      border-radius: 5px;
      &:hover {
        cursor: pointer;
        filter: brightness(0.9);
      }
    }
    &__del {
      background-color: rgb(226, 39, 39);
      color: #ffffff;
      border: none;
      width: 60px;
      padding: 5px;
      border-radius: 5px;
      margin-left: 5px;
      cursor: pointer;
      &:hover {
        cursor: pointer;
        filter: brightness(0.9);
      }
    }
    &__update {
      background-color: #2db14e;
      color: #ffffff;
      border: none;
      padding: 5px 35px;
      border-radius: 5px;
      &:hover {
        cursor: pointer;
        filter: brightness(0.9);
      }
    }
  }
}
</style>
