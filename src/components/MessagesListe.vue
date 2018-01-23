<template>

  <div>

    <nav-bar></nav-bar>

    <section class="section coop-accueil">
    <br><br>
        <div class="channel">

          <div class="panel">
            <message v-for="unMessage in liste" :mess="unMessage"></message>

          </div>

          <div class="control">
            <input @keyup.enter="envoyer" v-model="message" class="input" type="text">
            <button class="button" @click="envoyer">Envoyer</button>
          </div>

        </div>

    </section>

  </div>

</template>

<script>

import NavBar from './navBar.vue'
import Message from './message.vue'

export default {
  name: 'MessagesListe',
  components: {NavBar, Message},
  data () {
    return {
      liste : [],
      message : '',
    }
  },
  mounted() {
    window.axios.get('channels/'+this.$route.params.id+'/posts').then((response) => {
      this.liste = response.data;
    }).catch((error) => {
    });
  },
  methods : {
    envoyer() {
      window.axios.post('channels/'+this.$route.params.id+'/posts',{

        message : this.message,

      }).then((response) => {

        window.axios.get('channels/'+this.$route.params.id+'/posts').then((response) => {
          this.liste = response.data;
          this.message = '';
        }).catch((error) => {
        });

      }).catch((error) => {

        alert(error);

      });

    }
  }
}
</script>
