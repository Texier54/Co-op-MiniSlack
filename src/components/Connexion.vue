<template>

  <div class="modal-card">
    <header class="modal-card-head"><p class="modal-card-title">Co'op - Identification</p></header>

    <section class="modal-card-body">

      <form @submit="seConnecter">

        <label class="label">Email</label>
        <div class="field">
          <input class="input" v-model="email" type="text" placeholder="Email">
        </div>

        <label class="label">Mot de passe</label>
        <div class="field">
          <input class="input" v-model="password" type="password" placeholder="Mot de passe">
        </div>

        <div class="field">

          <div>
            <input type="submit" class="button is-success" value="Connexion">
          </div>

          <router-link class="button is-text" to="/membre-creation">Créer un compte</router-link>

        </div>

      </form>

    </section>

  </div>

</template>

<script>
export default {
  name: 'Connexion',
  data() {
    return {
      email : 'yt@google.com',
      password : 'yt',
    }
  },
  methods : {
    seConnecter() {
      window.axios.post('members/signin',{

        email : this.email,
        password : this.password

      }).then((response) => {

        this.$store.commit('setMember', response.data);
        this.$store.commit('setToken',response.data.token);

          axios.get('members').then((response) => {
            this.$store.commit('setListeMember',response.data);
          }).catch((error) => {
          });


        window.axios.defaults.params.token = response.data.token;

        this.$router.push({path: '/'});

      }).catch((error) => {

        alert(error.response.data.error.join("\n"));

      });

    }
  }
}

</script>

<style>
</style>
