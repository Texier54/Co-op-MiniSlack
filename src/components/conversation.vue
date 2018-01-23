<template>

<div class="panel-block">

    <router-link :to="{ name:'messages', params : { id : conv._id } }">
      <b>{{ conv.label }}</b>
    </router-link>

    <span class="tag">
      {{ conv.topic }}
    </span>

    <span class="panel-icon">
      <router-link :to="{ name:'conversation-modification', params : { id : conv._id } }">
        <i class="icon-edit"></i>
      </router-link>
    </span>

    <span class="panel-icon">
      <a @click="suprConv">
        <i class="icon-trash"> </i>
      </a>
    </span>

  </div>

</template>

<script>

export default {
  name: 'conversation',
  props : ['conv'],
  data () {
    return {
    }
  },
  methods : {
    suprConv() {

        window.axios.delete('channels/'+this.conv._id);
        window.bus.$emit('updateConv');
    }
  }


}
</script>
