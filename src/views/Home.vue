<template>
  <div class="ion-page">
    <ion-header>
      <ion-toolbar>
        <ion-title>ZipInfo</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content class="ion-padding">
      <ZipSearch v-on:get-zip="getZipInfo"/>
    </ion-content>
  </div>
</template>


<script>
import ZipSearch from "../components/ZipSearch";
export default {
  name: "home",
  components: { ZipSearch },
  methods: {
    getZipInfo(zip) {
      console.log(zip);
    }
  }
};
</script>
