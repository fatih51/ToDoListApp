<template>
    <div class="append">
        <input type="text" v-model="toDo" @keypress.enter="addToDo">
        <button type="submit" @click="addToDo">Append</button>
    </div>
</template>

<script>
export default {
    data (){
        return {
            toDo:"",
        }
    },
    methods : {
        addToDo(){
            this.$emit("isApended", this.toDo )
        },
    }
}
</script>

<style scoped>
.append{
    margin-left: 610px;
    margin-top: 25px;
}
.append input{
    border-radius: 5px;
    width: 500px;
    height: 100px;
    font-size: 20px;
}
.append button {
    width: 250px;
    height: 100px;
    font-size: 20px;
    color: white;
    background-color: #2196f3;
    border-radius: 10px;
    border: none;
}
.append button:hover{
    cursor: pointer;
}
</style>
