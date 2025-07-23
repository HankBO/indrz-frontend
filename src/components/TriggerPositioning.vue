<template>
  <div id="indrz-positioning" class="ol-control ol-unselectable positioning">
    <button class="default" title="Trigger Positioning" />
  </div>
</template>

<script>
import Control from 'ol/control/Control';
import MapHandler from '~/util/mapHandler';

export default {
  name: 'TriggerPositioning',
  props: {
    map: {
      type: Object,
      default: function () {
        return {};
      }
    },
    positionLabel: {
      type: Object,
      default: function () {
        return {};
      }
    }
  },
  data () {
    return {
    };
  },
  computed: {
    positionButton () {
      const container = document.getElementById('indrz-positioning');
      const button = container.getElementsByTagName('button');
      const classList = button[0].classList;
      return {
        container,
        button,
        classList
      }
    }
  },
  watch: {
    map: function (newValue) {
      this.addControl();
    }
  },
  mounted () {
  },
  methods: {
    addControl () {
      this.positionButton.container.addEventListener('click', () => {
        const isActiveButton = this.positionButton.classList.contains('active');
        if (!isActiveButton) {
          MapHandler.updatePositionLabel(this.positionLabel, [-263383.28479042684, 6688462.802836553]);
          setTimeout(() => {
            MapHandler.closePositionLabel(this.positionLabel);
          }, 5000);
        }
      });

      this.map.addControl(new Control({
        element: this.positionButton.container
      }));
    }
  }
}
</script>

<style lang="scss" scoped>
  .positioning {
    right: 10px !important;
    bottom: 120px !important;
    button {
      background-image: url('~@/static/images/icons/mylocation-sprite-1x.png');
      background-repeat: no-repeat;
      background-color: rgba(255,255,255,0.5);
    }
    .default {
      background-position: 3px 3px;
    }
    .active {
      background-position: -159px 3px;
    }
  }

</style>