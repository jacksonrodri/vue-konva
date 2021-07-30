<template>
  <b-card>
    <v-stage :config="config">
      <v-layer>
        <v-circle
          v-for="(item, i) in items"
          :key="i"
          :ref="`circle_${i}`"
          :config="item"
        />
      </v-layer>
    </v-stage>
  </b-card>
</template>

<script>
import Konva from "konva";
export default {
  props: {
    items: {
      type: Array,
      default: function () {
        return []
      }
    },
    config: {
      type: Object,
      default: function () {
        return {}
      }
    }
  },
  mounted() {
    for (let i = 0; i < this.items.length; i++) {
      const node = this.$refs[`circle_${i}`][0].getNode();
      const period = 1000;
      const amplitude = 10;
      const anim = new Konva.Animation((frame) => {
        node.setX(
          amplitude * Math.sin((frame.time * 2 * Math.PI) / period) +
            this.items[i].x
        );
      }, node.getLayer());

      anim.start();
    }
  },
};

</script>