<template>

  <div class="modal-card">
    <header class="modal-card-head"><p class="modal-card-title">Modification</p></header>

    <section class="modal-card-body">

      <form @submit="modifConversation">

        <div class="field">
          <input class="input" type="text" v-model="label" placeholder="Nom">
        </div>

        <div class="field">
          <input class="input" type="text" v-model="topic" placeholder="Description">
        </div>

        <input class="button is-primary" type="submit" value="Modifier">

        <router-link class="button is-text" to="/conversations"><i class="icon-remove">&nbsp;</i>Annuler</router-link>

      </form>
    </section>
  </div>
</template>

<script>
export default {
  name: 'ConversationModification',
  data () {
    return {
      label: '',
      topic: ''
    }
  },
  mounted() {
    window.axios.get('channels/'+this.$route.params.id).then((response) => {
      this.label = response.data.label;
      this.topic = response.data.topic;
    }).catch((error) => {
    });
  },
  methods : {
    modifConversation() {
      window.axios.put('channels/'+this.$route.params.id,{

        label : this.label,
        topic : this.topic,

      }).then((response) => {

      	this.$router.push({path: '/conversations'});

      }).catch((error) => {

        alert(error);

      });

    }
  }
}
</script>
