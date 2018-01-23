<template>


<nav class="navbar has-shadow is-fixed-top navbar is-link navbar-principale">
  <div class="navbar-brand"><a href="/" class="navbar-item">
    <b>Co'op</b>
    </a>
  </div>

  <div class="navbar-item">
    <a href="#/conversations" class="navbar-item router-link-exact-active router-link-active is-active">
      <i class="fa fa-comment"></i>
      Conversations
    </a>
  </div>

  <div class="navbar-item">
    <a href="#/members" class="navbar-item"><i class="fa fa-user"></i>
      Membres
    </a>
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