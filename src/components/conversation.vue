<template>

<div class="panel-block">

  <a href="" class="">

    <router-link :to="{ name:'messages', params : { id : conv._id } }">
      <b>{{ conv.label }}</b>
    </router-link>

    <span class="tag">
      {{ conv.topic }}
    </span>

    <router-link :to="{ name:'conversation-modification', params : { id : conv._id } }">
      Modifier
    </router-link>

    <a>
      <i class="icon-trash"> </i> </span>
    </a>

  </a>

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

}
</script>