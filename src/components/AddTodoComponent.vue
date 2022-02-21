<template>
  <div class="add-to-do-component">
      <input class="add-to-do-component__input" type="text" placeholder="Nhập công việc cần thêm..." v-model="titleInput" />
      
      <button class="add-to-do-component__btn" @click="onAddTodo" :class="isDisabled ? 'is-disabled' : '' ">Thêm</button>
  </div>
</template>

<script>
export default {
    data() {
        return {
            titleInput: "",
            isDisabled: false,
        }
    },
    methods: {
        onAddTodo() {
            this.$emit('on-add-todo', this.titleInput)
            console.log(this.titleInput);
            this.titleInput ='';
        }
    }
}
</script>

<style lang="scss" scoped>
    .add-to-do-component {
        margin-top: 60px;
        height:50px;
        width: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
        &__input{
            height: 100%;
            padding: 10px;
            width: 85%;
            margin-right: 30px;
            border: none;
            border-radius: 5px;
            font-size: 16px;
            box-shadow: 0 0 10px 2px rgba(0, 0, 0, 0.2);

        }
        &__btn {
            height: 100%;
            min-width: 130px;
            border-radius: 5px;
            border: none;
            font-weight: bold;
            font-size: 16px;
            color: #ffffff;
            background-color: #2db14e;
            box-shadow: 0 0 10px 2px rgba(0, 0, 0, 0.2);
            &:hover {
                cursor: pointer;
                filter: brightness(0.9);
            }
            &.is-disabled {
                cursor: not-allowed;
                background-color: #EFEFEF;
                color: #cccccc;
            }
        }
    }
</style>