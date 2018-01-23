<template>

<div class="panel-block">

  <figure class="media-left">
    <p class="image is-32x32">
      <img :src="result">
    </p>
  </figure>

  <b>{{ memb.fullname }}</b>

  <span class="tag">
    {{ memb.email }}
  </span>

</div> 

</template>

<script>

import md5 from 'js-md5';

export default {
  name: 'member',
  props : ['memb'],
  data () {
    return {
      result: '',
    }
  },
  mounted () {
    this.result = 'https://www.gravatar.com/avatar/'+md5(this.memb.email)+'?d=https://api.adorable.io/avatars/285/abott@adorable.png';
  },

}
</script>