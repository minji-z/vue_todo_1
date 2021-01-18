<template>
	<div class="todoInput">
        <input type="text" class= "inp" @keyup.enter="addTodo" v-model="newTodoItem">
        <button @click="addTodo">add</button>
    </div>
</template>

<script>
export default{
    data() {
        return {
            newTodoItem : ''
        }
    },
    methods: {
        addTodo(){
            if(this.newTodoItem !== ''){
                var value = this.newTodoItem && this.newTodoItem.trim();
                this.$emit('addTodo', value);
                this.clearInp();
            }
        },
        clearInp(){
            this.newTodoItem = '';
        }
    }
}
</script>

<style scoped>
.inp{
    width: 300px;
}
</style>