<template>

  <article class="media channel-message">

    <figure class="media-left">
      <p class="image is-32x32">
        <img :src="result">
      </p>
    </figure>


    <div class="media-content">
      <strong>{{ member.fullname }}</strong> 
      <small>{{ member.email }}</small> 
      <span title="2017-12-15T10:56:48.975+01:00" class="date"> 22m</span> 
      <br> 

      <div>
        {{ mess.message }}
      </div>

    </div> 

  </article>

</template>

<script>

import md5 from 'js-md5';

export default {
  name: 'message',
  props : ['mess'],
  data () {
    return {
      member: '',
      result: '',
    }
  },
  mounted() {

    var obj = this.$store.state.listemember;

    for (var prop in obj) {
      if(obj[prop]['_id'] == this.mess.member_id)
        this.member = obj[prop];
    }

    this.result = 'https://www.gravatar.com/avatar/'+md5(this.member.email)+'?d=https://api.adorable.io/avatars/285/abott@adorable.png';
  },

}
</script>