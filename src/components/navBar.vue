<template>
<nav class="navbar is-link">
  <div class="navbar-brand">
    <a href="/" class="navbar-item">
      <b class="is-size-2"><i class="marker fas fa-map-marker-alt"></i>Co'op</b>
    </a>
    <button class="button navbar-burger btnreduc" data-target="navMenu">
      <span></span>
      <span></span>
      <span></span>
    </button>   
  </div>
  <div class="navbar-menu" id="navMenu">

    <div class="navbar-item">
      <router-link class="navbar-item" to="/conversations">Conversations</router-link>
    </div>

    <div class="navbar-item">
      <router-link class="navbar-item" to="/members">Membres</router-link>
    </div>

    <div class="navbar-end">
      <a class="navbar-item" @click="logOut">Se déconnecter</a>
    </div>

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
  },

  mounted(){
    // Get all "navbar-burger" elements
  var $navbarBurgers = Array.prototype.slice.call(document.querySelectorAll('.navbar-burger'), 0);

  // Check if there are any navbar burgers
  if ($navbarBurgers.length > 0) {

    // Add a click event on each of them
    $navbarBurgers.forEach(function ($el) {
      $el.addEventListener('click', function () {

        // Get the target from the "data-target" attribute
        var target = $el.dataset.target;
        var $target = document.getElementById(target);

        // Toggle the class on both the "navbar-burger" and the "navbar-menu"
        $el.classList.toggle('is-active');
        $target.classList.toggle('is-active');

      });
    });
  }

  },

}
</script>

<style>
.router-link-exact-active {
  background-color:#fff;
  color: #1abc9c;
}

.navbar-burger {
  margin-bottom: auto;
  margin-top: auto;
}

.is-active .btn {
  margin-left: 10px;
}

</style>