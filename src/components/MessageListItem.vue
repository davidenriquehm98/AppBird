<template>
  <ion-item v-if="message" :detail="false" class="list-item">
    <ion-label class="ion-text-wrap">
      <ion-img
        src="/70.png"
        alt="icon"
        class="iconSound"
      ></ion-img>
      <h2>Familia: {{ message.group }}</h2>
      <h2>Nombre: {{ message.en }}</h2>
      <h3>Ubicación: {{ message.loc }}</h3>
      <h3>Descubridor: {{ message.rec }}</h3>
    </ion-label>
  </ion-item>
</template>

<script setup lang="ts">
import { IonIcon, IonItem, IonLabel, IonNote } from "@ionic/vue";
import { chevronForward } from "ionicons/icons";

defineProps({
  message: Object,
});

const isIos = () => {
  const win = window as any;
  return win && win.Ionic && win.Ionic.mode === "ios";
};
</script>

<style scoped>
.list-item {
  --padding-start: 0;
  --inner-padding-end: 0;
}

.list-item ion-label {
  margin-top: 12px;
  margin-bottom: 12px;
}

.list-item h2 {
  font-weight: 600;
  margin: 0;

  /**
   * With larger font scales
   * the date/time should wrap to the next
   * line. However, there should be
   * space between the name and the date/time
   * if they can appear on the same line.
   */
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}

.list-item p {
  text-overflow: ellipsis;
  overflow: hidden;
  white-space: nowrap;
  width: 95%;
}

.list-item .date {
  align-items: center;
  display: flex;
}

.list-item ion-icon {
  color: #c9c9ca;
}

.list-item ion-note {
  font-size: 0.9375rem;
  margin-right: 8px;
  font-weight: normal;
}

.list-item ion-note.md {
  margin-right: 14px;
}

.list-item .dot {
  display: block;
  height: 12px;
  width: 12px;
  border-radius: 50%;
  align-self: start;
  margin: 16px 10px 16px 16px;
}

.list-item .dot-unread {
  background: var(--ion-color-primary);
}

.ion-text-wrap {
  display: flex;
  flex-wrap: wrap;
  text-align: center;
  justify-content: center;
  align-items: center;
}

.ion-text-wrap h2, .ion-text-wrap h3 {
  width: 100%;
  text-align: center;
  justify-content: center;
  align-items: center;
}

.ion-text-wrap .iconSound {
  height: 5rem !important;
  width: 5rem !important;
  border-radius: 1rem;
}

.ion-text-wrap .iconSound img{
  border-radius: 1rem;
}
</style>
