<template>

  <div>

    <nav-bar></nav-bar>

    <section class="section coop-accueil">
    <br><br>
          <div class="panel">

          <p class="panel-heading">
            Conversations
            <a class="button is-small" href="#/newConv"><span class="icon"><i class="fa fa-plus"></i></span>
              <span>
                Nouvelle conversation
              </span>
            </a>
          </p>

          <conversation v-for="uneConv in liste" :conv="uneConv"></conversation>
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
  }
}
</script>

