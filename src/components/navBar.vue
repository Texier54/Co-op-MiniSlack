<template>


<nav class="navbar has-shadow is-fixed-top navbar is-link navbar-principale">
  <div class="navbar-brand"><a href="/" class="navbar-item">
    <b>Co'op</b>
    </a>
  </div>

  <div class="navbar-item">
    <router-link class="navbar-item" to="/conversations">Conversations</router-link>
  </div>

  <div class="navbar-item">
    <router-link class="navbar-item" to="/members">Membres</router-link>
  </div>

  <div class="navbar-end">
    <a class="navbar-item" @click="logOut">Se déconnecter</a>
  </div>

  </nav>
    


</template>

<script>

export default {
  name: 'navBar',

  data () {
    return {
    }
  },

  methods : {
    logOut() {
      window.bus.$emit('logout');
    }
  }

}
</script>

<style>
.router-link-exact-active {
  background-color:#fff;
  color: #1abc9c;
}
</style>