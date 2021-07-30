<template>
  <div>
    <div
      v-for="item in multiItems"
      :key="item.id"
    >
      <individual-konva
        :items="item.items"
        :config="item.configKonva"
      />
    </div>
  </div>
</template>

<script>
import IndividualKonva from '../components/IndividualKonva.vue';
import data from '../assets/data.json';
export default {
  components: { IndividualKonva },
  data() {
    return {
      multiItems: data.multiItems
    };
  },
};

</script>