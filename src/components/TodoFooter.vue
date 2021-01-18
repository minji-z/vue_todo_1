<template>
	<div class="todoFooter">
        <button type="button" @click="clearTodo">clear</button>
    </div>
</template>

<script>
export default{
    methods:{
        clearTodo(){
            this.$emit('removeAll');
        }
    }
}
</script>

<style scoped>
.todoFooter{
    margin-top: 10px;
    text-align:center;
}
</style>