<template>
	<header class="header">
        <h2>TodoList</h2>
        <h4>{{ timeStamp }}</h4>
    </header>
</template>

<script>
import getDate from "../assets/commonJS/getDate.js";

export default {
    data(){
        return{
            timeStamp: ""
        };
    },
    created() {
        this.timeStamp =  `${getDate().month}월${getDate().date}일 ${getDate().week}`;
    }
};
</script>

<style scoped>
.header{
    text-align: center;
    margin-top: 50px;
}
h2, h4{
    display: inline;
}
h4{
    color: gray;
}
</style>
