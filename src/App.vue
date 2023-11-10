<template>
 <div id="app">
    <todoInput @addTask="addTask"></todoInput>
 <todolist :todolist="todolist"></todolist>
<todoButton @clickChange="clickChange"></todoButton>

 </div>
</template>

<script>
import todolist from './components/todolist.vue'
import todoButton from './components/todoButton.vue'
import todoInput from './components/todoInput.vue'
export default {
name:"app",
data(){
    return {
     todolist: [
        {id:1,task:'睡觉',isCompleted:true},
        {id:2,task:'吃饭',isCompleted:false},
        {id:3,task:'喝茶',isCompleted:true},
     ],
     active:0,
    }
},
computed:{
 todolist(){
    if(this.active===0){
        return this.todolist
    }else if(this.active===1){
        return this.todolist.filter(item=>item.isCompleted)}
        else{
            return this.todolist.filter(item=>!item.isCompleted)
        }
    }
 },

methods:{
    clickChange(active){
        this.active=active
        console.log(this.active)
    },
    addTask(taskname){
        this.todolist.push({
            id:this.todolist.length+1,
            task:taskname,
            isCompleted:false,
        })

    }
},
components:{
    todolist,
    todoButton,
    todoInput,
},
}
</script>
<style>

</style>
