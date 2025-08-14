<template>
  <div id="position-label" :style="{'min-width': '354px'}" scrollable title="position label" class="ol-popup position-label">
    <img  src="/images/selected-large.png" />
  </div>

</template>

<script>
export default {
  name: 'PositionLabel',
  data () {
  }
};
</script>

<style scoped>
  #position-label{
    position: absolute;
    bottom: 0;
    left: -20px;
    z-index: 1;
  }
</style>