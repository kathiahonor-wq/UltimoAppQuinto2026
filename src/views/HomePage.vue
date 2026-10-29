<template>
  <ion-page>
    <ion-header>
      <ion-toolbar color="dark">
        <ion-title>Ejercicios basicos</ion-title>
      </ion-toolbar>
     </ion-header>
    <ion-content >
      <h1>las cuatro operaciones</h1>
      <ion-item>
        <p>Suma: {{ a }} + {{ b }}= {{ a+b }}</p>
        <p>Resta: {{ a }} - {{ b }}= {{ a-b }}</p>
        <p>Multiplicación: {{ a }} * {{ b }}= {{ a*b }}</p>
        <p>División: {{ a }} / {{ b }}= {{ a/b }}</p>
      </ion-item>
      <ion-item>
       <ion-input label="Ingrese a:" placeholder="Ingrese un número" type="number" v-model.number="a"></ion-input>
       <ion-input label="Ingrese b:" placeholder="Ingrese otro número" type="number" v-model.number="b"></ion-input>
      </ion-item>
       <ion-item>
        <ion-input label="Ingrese nombre:" placeholder="Ingrese un nombre" type="text" v-model="nombre"></ion-input>
       <ion-input label="Ingrese edad:" placeholder="Ingrese la edad" type="number" v-model.number="edad"></ion-input>
      </ion-item>
      <ion-item>
        <ion-button color="danger" @click="AdicionarEst()">
          Adicionar estudiante
        </ion-button>
        <ion-button color="warning" @click="AddStudent">
          Adicionar estudiante
        </ion-button>
      </ion-item>
      <ion-item v-if="a === 0">
        <p>a debe ser diferente de cero.</p>
      </ion-item>
      <ion-item v-if="b === 0">
        <p>b debe ser diferente de cero.</p>
      </ion-item>
      <h1>Lista de estudiantes</h1>
      <ion-list>
        <ion-item v-for="(est, index) in estudiantes" :key="est.nombre">
          <p>{{ index + 1 }}.</p>
          <p>  {{ est.nombre }}</p>
          <p>  Edad: {{ est.edad }}</p>
        </ion-item>
      </ion-list>
    </ion-content>
  </ion-page>
</template>

<script setup lang="ts">
import { IonButton, IonContent, IonHeader, IonInput, IonItem, IonList, IonPage, IonTitle, IonToolbar } from '@ionic/vue';
import { ref } from 'vue';
const a = ref(15);
const b = ref(3);
const estudiantes = ref([
  { nombre: "Juan", edad: 20 },
  { nombre: "María", edad: 22 },
  { nombre: "Pedro", edad: 19 },
]);
const nombre = ref('');
const edad = ref(0);
const AddStudent = () => {
 estudiantes.value.push(
 {
    nombre: nombre.value,
    edad: edad.value,
  } 
  );
nombre.value = '';
  edad.value = 0;
};
function AdicionarEst()   
{
alert("Adicionando estudiante2"); 
};

</script>

<style scoped>
#container {
  text-align: center;
  
  position: absolute;
  left: 0;
  right: 0;
  top: 50%;
  transform: translateY(-50%);
}

#container strong {
  font-size: 20px;
  line-height: 26px;
}

#container p {
  font-size: 16px;
  line-height: 22px;
  
  color: #8c8c8c;
  
  margin: 0;
}

#container a {
  text-decoration: none;
}
</style>
