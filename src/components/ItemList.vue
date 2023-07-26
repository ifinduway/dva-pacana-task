<template>
  <div>
    <h2>{{ title }}</h2>
    <div class="items">
      <button
        v-for="item in items"
        :key="item.id"
        @click="handleItemClick(item)"
        :class="{ 'selected-item': isSelected(item) }"
      >
        {{ item.name }}
      </button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      default: '',
    },
    items: {
      type: Array,
      default: () => [],
    },
    maxSelect: {
      type: Number,
      default: 1,
    },
  },

  data() {
    return {
      selectedItems: [],
    };
  },

  watch: {
    selectedItems(newVal) {
      this.$emit('select', newVal);
    },
  },
  methods: {
    handleItemClick(item) {
      const index = this.selectedItems.findIndex((selected) => selected.id === item.id);

      if (index === -1) {
        if (this.maxSelect > this.selectedItems.length) {
          this.selectedItems.push(item);
        }
      } else {
        this.selectedItems.splice(index, 1);
      }
    },
    isSelected(item) {
      return this.selectedItems.some((selected) => selected.id === item.id);
    },
  },
};
</script>

<style>
.items {
  border: 1px solid #ccc;
  padding: 10px;
  max-height: 200px;
  overflow-y: auto;
}

.selected-item {
  background-color: #f0f0f0;
}
</style>
