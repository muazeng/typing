<script >
import Menu from './LessonsMenu.vue';
import TestCanvas from './TestCanvas.vue';
import axios from 'axios'
export default {
    data:()=>{
        return {
            message:""
        }
    },
    components:{ Menu, TestCanvas }
    ,
    methods:{
            async fetchdata(){
                var resp= await axios.get('http://localhost:3000/users');
                console.log(resp.data)
                
            }
        }
}
</script>

<template>
    <div id="main">
        <div id="menuList"> <Menu  /></div>
       
       
        <div id="panel">
        
            <TestCanvas 
            timer="200"
            trainText="اااا معاذ اااا ببيييب
ااااا ببببب ااااا بببببب
ااااا ببببب ااااا بببببب
ااااا ببببب ااااا بببببب
ااااا ببببب ااااا بببببب
ااااا ببببب ااااا بببببب
ااااا ببببب ااااا بببببب
ااااا ببببب ااااا بببببب
ااااا ببببب ااااا بببببب
ااااا ببببب ااااا بببببب
ااااا ببببب ااااا بببببب
ااااا ببببب ااااا بببببب
ااااا ببببب ااااا بببببب
ااااا ببببب ااااا بببببب
ااااا ببببب ااااا بببببب
ااااا ببببب ااااا بببببب
ااااا ببببب ااااا بببببب
ااااا ببببب ااااا بببببب
ااااا ببببب ااااا بببببب
ااااا ببببب ااااا بببببب
ااااا ببببب ااااا بببببب
ااااا ببببب ااااا بببببب
ااااا ببببب ااااا بببببب"/>
        </div>

        <button @click="fetchdata">hello</button>
    </div>
   
</template>




<style>
    #main{
        display: grid;
        grid-template-columns: 1fr 5fr 2fr;
        column-gap: 5em;
        height: 70%;

    }
    #menuList{
        height: 100%;
        overflow: scroll;
        font-size: .8em;
    }
</style>
