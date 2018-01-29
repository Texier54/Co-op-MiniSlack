<template>

  <div>

    <nav class="navbar is-primary is-fixed-top">
      <div class="navbar-item">
        <a href="#/conversations" class="button is-small">
          <span class="icon">
            <i class="icon-angle-left"></i>
          </span>
          <span>Retour</span>
        </a>
      </div>

      <div class="navbar-end">
        <div class="navbar-item">
          <button @click="refresh" class="button is-small is-danger">
              Rafraichir
          </button>
        </div> 
      </div>

    </nav>

    <section class="section coop-accueil">
        <div class="channel">

          <div class="panel">
            <message v-for="unMessage in liste" :mess="unMessage"></message>

          </div>

        </div>

    </section>

    <section id="pagination" class="navigation is-fixed-bottom">
      <input @keyup.enter="envoyer" v-model="message" class="input is-medium" type="text">
      <button class="button" @click="envoyer">Envoyer</button>
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
      setTimeout(function(){ window.scrollTo(0,document.body.scrollHeight); }, 300);
    }).catch((error) => {
    });


    window.bus.$on('updateMessage',() => {
      window.axios.get('channels/'+this.$route.params.id+'/posts').then((response) => {
        this.liste = response.data;
      }).catch((error) => {
      });
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

        setTimeout(function(){ window.scrollTo(0,document.body.scrollHeight); }, 100);

      }).catch((error) => {

        alert(error);

      });
    },

    refresh() {
      window.axios.get('channels/'+this.$route.params.id+'/posts').then((response) => {
        this.liste = response.data;

        setTimeout(function(){ window.scrollTo(0,document.body.scrollHeight); }, 100);

        
      }).catch((error) => {
      });
    }
  },
}
</script>
