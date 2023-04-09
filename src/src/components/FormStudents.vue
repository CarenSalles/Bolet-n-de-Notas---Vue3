<script setup>
 import {ref} from 'vue';

 let students = ref([]);
 let studentAdded = ref({
     name: "",
     subject: "",
     score: "",
 });

 function AddStudent(){

    if (studentAdded.value.name.trim() === "" ||
    studentAdded.value.subject.trim() === "" ||
    isNaN(studentAdded.value.score)
    ) {
        return alert("Los campos deben ser completados!");
    }
    students.value.push(studentAdded.value);
    studentAdded.value = {name: "", subject:"", score:""};

    
 }
</script>

<template>
    <div class="wrapper">
      <header>
        <h1>School Grades</h1>
      </header>
      <form class="wrapper__form">
        <input type="text" placeholder="Name"/>
        <input type="text" placeholder="Subject"/>
        <input type="number" placeholder="Score"/>
        <button type="submit">Add+</button>
      </form>
      <table class="wrapper__table">
        <thead class="wrapper__table__title">
            <tr>
                <td>Name</td>
                <td>Subject</td>
                <td>Score</td>
            </tr>
        </thead>
        <tbody class="wrapper__table__show">
            <tr>
                <td></td>
                <td></td>
                <td></td>
            </tr>
        </tbody>
      </table>
    </div>
</template>

<style lang="scss">

.wrapper{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 100%;
    height: 80%;

    &__form{
        display: flex;
        flex-direction: column;
        // justify-content: center;
        align-items: center;
        background-color: rgb(43, 178, 137);
        // width: auto 0;
        // height: auto 0;
        border-radius: 0.5vh;

       input{
        display: flex;
        margin: 1em;                                
        font-size: 1.2em;
        border-radius: 0.5vh;
        border: none;        
       } 

       button{
           display: flex;
           background-color: rgb(255, 85, 0);
           border-radius: 0.5vh;
           border: none;
           font-size: 1em;
           padding: 0.8vh;
           margin-bottom: 1em;
       }
    }
    &__table{
       display: flex;
       justify-content: center;
       background-color: cadetblue;
       width: 40%;
       margin: 2em;

       &__title{
        display: flex;
        flex-direction: column;
        align-items: center;
        font-size: 1.3em;
        font-weight: 500;

        tr{
            display: flex;
            flex-direction: row;
            // align-items: center;
            gap: 2em;
            // justify-content:center;
        }
       }
       &__show{
        font-size: 1.3em;
        font-weight: 200;
        position: absolute;
        margin: 1em;
       tr{
        gap: 1em;
       }
       }
    }
}




</style>