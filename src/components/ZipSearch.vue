<template>
  <ion-grid>
    <form @submit.prevent="onSubmit">
      <ion-col>
        <ion-item>
          <ion-label>Zipcode:</ion-label>
          <ion-input
            :value="zip"
            @input="zip = $event.target.value"
            placeholder="Enter US Zipcode"
            name="zip"
          ></ion-input>
        </ion-item>
      </ion-col>
      <ion-col>
        <ion-button type="submit" color="primary" expand="block">Find</ion-button>
      </ion-col>
    </form>
  </ion-grid>
</template>

<script>
export default {
  name: "ZipSearch",
  data() {
    return {
      zip: ""
    };
  },
  methods: {
    onSubmit() {
      // Zip Regex
      const isValidZip = /(^\d{5}$)|(^\d{5}-\d{4}$)/.test(this.zip);
      // Test for valid zip
      if (!isValidZip) {
        this.showAlert();
        this.zip = "";
      } else {
        this.$emit("get-zip", this.zip);
        this.zip = "";
      }
    },
    showAlert() {
      return this.$ionic.alertController
        .create({
          header: "Enter Zipcode",
          message: "Please enter a valid US zipcode",
          buttons: ["OK"]
        })
        .then(a => a.present());
    }
  }
};
</script>
