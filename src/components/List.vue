<template>
    <div class="list">
        <ul>
            <li v-for="item in todolist" :key="item.id">
                <div class="container">
                    <span>{{ item.data }}</span>
                    <span class="time">{{ item.time }}</span>
                    <button class="button" type="submit" @click="deleteItem(item)">Delete</button>
                    <hr>
                </div>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    props: ["todolist"],
    methods:{
        deleteItem(item){
            this.$emit("isDeleted",item.id)
        }
    }
}
</script>

<style scoped>
.list ul{
    list-style: none;
    font-size: 20px;
}
.container {
  flex-direction: row;
  margin-top: 100px;
}
.time {
    margin-left: 100px;
}
.button{
    margin-left:1000px;
    background-color: red;
    color:white;
    width: 80px;
    height: 40px;
    border: none;
    border-radius: 5px;
    font-size: 20px;
}
.button:hover{
    cursor: pointer;
}
</style>