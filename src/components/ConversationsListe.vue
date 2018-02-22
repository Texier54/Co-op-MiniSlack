<template>

  <div>

    <nav-bar></nav-bar>

    <section class="container section coop-accueil">

      <div class="columns">
        <div class="column is-12">

          <div class="panel">

            <p class="panel-heading">
              Conversations
              <a class="button" href="#/newConv"><span class="icon"><i class="icon-comment"></i></span>
                <span>
                  Nouvelle conversation
                </span>
              </a>
            </p>

            <conversation v-for="uneConv in liste" :conv="uneConv"></conversation>
          </div>
        </div>
      </div>

    </section>

  </div>

</template>

<script>

import NavBar from './navBar.vue'
import Conversation from './conversation.vue'

export default {
  name: 'ConversationsListe',
  components: {NavBar, Conversation},
  data () {
    return {
      liste : [],
    }
  },
  mounted() {
    window.axios.get('channels').then((response) => {
      this.liste = response.data;
    }).catch((error) => {
    });

    window.bus.$on('updateConv',() => {
      window.axios.get('channels').then((response) => {
        this.liste = response.data;
      }).catch((error) => {
      });
    });

  }
}
</script>
