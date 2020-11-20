<template>
  <div style="padding: 200px">
    <Hover closeDelay="500" v-slot:default="{ hover }">
<!-- <Hover openDelay="500" v-slot:default="{ hover }"> --> 
      <div
        style="width: 200px; height: 200px;"
        :style="{ background: hover ? 'red' : 'blue' }"
      ></div>
    </Hover>
  </div>
</template>

<script>
import Hover from './components/Hover.vue';

export default {
  components: { Hover },
}
</script>