<template>
	<div class="todoList">
        <ul class="list">
            <li v-for="(todoItem,index) in propsdata" :key="todoItem">
                {{ todoItem }}
                <button type="button" v-on:click="removeTodo(todoItem,index)">x</button>
            </li>
        </ul>
    </div>
</template>

<script>
export default{
    props: ['propsdata'],
    methods:{
        removeTodo(todoItem,index){
            this.$emit('removeTodo', todoItem, index);
        }
    }
}
</script>

<style scoped>
.list{
    text-align: left;
}
ul{
    list-style-type: none;
}
li{
    padding: 5px;
}
</style>