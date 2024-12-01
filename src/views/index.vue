<template>
  <ion-page class=" containerPage" >
    <div class="titulo" >
      <span>
        Inicio
      </span>
    </div>
    <div class="subtitulo" >
      <span>
        David Enrique Hernández Macajola
      </span>
    </div>
    <div class="subtitulo" >
      <span>
        23001604
      </span>
    </div>
    <div class="action" >
      <ion-button @click="cargar" >Cargar</ion-button>
    </div>
  </ion-page>
</template>

<script setup>
import { IonButton } from '@ionic/vue';
import { useRouter } from 'vue-router';

const router = useRouter();

const cargar = () => {
  router.push('home');
};

</script>


<style scoped>
.containerPage {
  display: flex;
  width: 100%;
  height: 85%;
  align-items: center;
  justify-content: center;
  flex-wrap: wrap;
  align-content: center;
}

.containerPage .titulo {
  width: 100%;
  font-weight: 700;
  font-size: 36px;
  padding: 2rem;
  text-align: center;
}

.containerPage .subtitulo {
  width: 100%;
  font-weight: 500;
  font-size: 18px;
  padding: 0.5rem;
  text-align: center;
}

.containerPage .action {
  display: flex;
  width: 100%;
  padding: 2rem;
  align-items: center;
  justify-content: center;
}

</style>


