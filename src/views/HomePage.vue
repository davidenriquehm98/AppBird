<template>
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-title>Aves de Guatemala</ion-title>
      </ion-toolbar>
    </ion-header>

    <ion-content :fullscreen="true">
      <ion-refresher slot="fixed" @ionRefresh="loadAves($event)">
        <ion-refresher-content></ion-refresher-content>
      </ion-refresher>

      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Aves de Guatemala</ion-title>
        </ion-toolbar>
      </ion-header>

      <ion-list>
        <MessageListItem
          v-for="item in itemsAves"
          :key="item.id"
          :message="item"
        />
      </ion-list>
    </ion-content>
  </ion-page>
</template>

<script setup lang="ts">
import {
  IonContent,
  IonHeader,
  IonList,
  IonPage,
  IonRefresher,
  IonRefresherContent,
  IonTitle,
  IonToolbar,
} from "@ionic/vue";
import MessageListItem from "@/components/MessageListItem.vue";
import { ref } from "vue";

const itemsAves = ref([]);

const loadAves = async (ev: CustomEvent) => {
  const url = "https://xeno-canto.org/api/2/recordings?query=cnt:guatemala";
  try {
    const response = await fetch(url);
    if (!response.ok) {
      throw new Error(`Response status: ${response.status}`);
    }

    const json = await response.json();
    // console.log(json);
    const arrayItems = json.recordings
    itemsAves.value = [...arrayItems]

    ev != null && ev.detail.complete();
  } catch (error) {
    console.error(error.message);
    ev != null && ev.detail.complete();
  }
};

loadAves();

</script>
