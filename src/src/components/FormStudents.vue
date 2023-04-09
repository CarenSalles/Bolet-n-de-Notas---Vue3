<script setup>
 import {ref} from 'vue';

 let students = ref([]);
 let studentAdded = ref({
     name: "",
     subject: "",
     score: "",
 });

 function AddStudent(){

    // Verifica que ningum campo este vacio.
    // arreglo los campos vacios.
    // El método trim() elimina los espacios en blanco de ambos lados de una cadena.
    // El método trim()método no cambia la cadena original.

    if (studentAdded.value.name.trim() === "" ||
    studentAdded.value.subject.trim() === "" ||
    isNaN(studentAdded.value.score)
    ) {
        return alert("Los campos deben ser completados!");
    }

    //El push()método agrega nuevos elementos al final de una matriz.
    //El push()método cambia la longitud de la matriz.
    //El push()método devuelve la nueva longitud.
    
    students.value.push(studentAdded.value);
    studentAdded.value = {name: "", subject:"", score:""};

 }

 function baremoScore(score) {
    if (score >= 0 && score < 3) {
        return "Muy deficiente";
    }

    if (score >= 3 && score < 5) {
        return "Insuficiente";
    }

    if (score >= 5 && score < 6) {
        return "Suficiente";
    }

    if (score >= 6 && score < 7) {
        return "Bien";
    }

    if (score >= 7 && score < 9) {
        return "Notable";  
    }

    if (score >= 9 && score <= 10) {
        return "Sobresaliente";  
    }
     
    if (score > 10) {
        return alert ("Nota erronea!")
        
    }
 }
</script>

<template>
    <!-- // @submit.prevent El evento de enviar ya no volverá a cargar la página y solo el modificador -->
    <!-- v-model: en Vue 3 es la posibilidad de atacar una prop de un componente a través de v-model para que cuando su valor cambie podamos capturarlo desde el componente que lo utiliza. -->
    <!-- data-binding es la posibilidad de que cuando un input cambie desde nuestro formulario p.ej también lo haga en nuestro componente. -->
    
    <div class="wrapper">
      <header>
        <h1>School Grades</h1>
      </header>
      <form @submit.prevent="AddStudent" class="wrapper__form">
        <input type="text" placeholder="Name" v-model="studentAdded.name"/>
        <input type="text" placeholder="Subject" v-model="studentAdded.subject"/>
        <input type="number" placeholder="Score" v-model="studentAdded.score"/>
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
            <tr v-for="student in students" :key="student.id">
                <td>{{ student.name }}</td>
                <td>{{ student.subject }}</td>
                <td>{{ baremoScore(student.score) }}</td>
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