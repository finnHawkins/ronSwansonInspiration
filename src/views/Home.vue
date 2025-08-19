<template>
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-title>Blank</ion-title>
      </ion-toolbar>
    </ion-header>
    
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">What Would Ron Swanson Do?</ion-title>
        </ion-toolbar>
      </ion-header>
    
      <div id="container">
        <img src="https://images.immediate.co.uk/production/volatile/sites/3/2016/08/115819.jpg?quality=90&resize=561%2C374">
        <h1>{{ swansonQuote }}</h1>
        <ion-button v-on:click="getQuote()">I need more motivation.</ion-button>
      </div>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { IonContent, IonHeader, IonPage, IonTitle, IonToolbar } from '@ionic/vue';
import { defineComponent } from 'vue';
import axios from 'axios';

export default defineComponent({
  name: 'Home',
  components: {
    IonContent,
    IonHeader,
    IonPage,
    IonTitle,
    IonToolbar
  },
  data: function() {
    return {
      swansonQuote: ''
    }

  },

  methods: {

    getQuote: function() {

      const axios = require("axios").default;

      const options = {
          method: 'GET',
          url: 'https://ron-swanson-quotes.herokuapp.com/v2/quotes',
      };

        axios.request(options).then(resp => {
          this.swansonQuote = resp.data[0];
        })
        .catch(err => {
            // Handle Error Here
            console.error(err);
        });

    }

  }


});
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