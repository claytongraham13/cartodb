<template>
  <SimpleMapCard
    v-if="!condensed"
    :visualization="visualization"
    :isSelected="isSelected"
    :canHover="canHover"
    :selectMode="selectMode"
    @toggleSelection="toggleSelection"/>
  <CondensedMapCard
    v-else
    :visualization="visualization"
    :isSelected="isSelected"
    :canHover="canHover"
    :selectMode="selectMode"
    @toggleSelection="toggleSelection"/>
</template>

<script>
import CondensedMapCard from './CondensedMapCard';
import SimpleMapCard from './SimpleMapCard';
import props from './shared/props';

export default {
  name: 'MapCard',
  props: {
    ...props,
    condensed: {
      type: Boolean,
      default: false
    }
  },
  components: {
    SimpleMapCard,
    CondensedMapCard
  },
  methods: {
    toggleSelection ($event) {
      this.$emit('toggleSelection', {
        map: this.$props.visualization,
        isSelected: !this.$props.isSelected,
        event: $event
      });
    }
  }
};
</script>
