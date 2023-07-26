<template>
  <div class="selected-items">
    <h3>{{ title }}</h3>
    <ul>
      <li v-for="item in selectedItems" :key="item.id">{{ item.name }}</li>
    </ul>
    <div v-if="counter" class="selected-items__counter">
      {{ `${this.selectedItems.length}/${this.counter}` }}
    </div>
  </div>
</template>

<script>
export default { 
  props: {
    title: {
      type: String,
      default: 'test title',
    },
    selectedItems: {
      type: Array,
      default: () => [],
    },
    counter: {
      type: Number,
      default: 0,
    },
  },
};
</script>

<style lang="scss">
.selected-items {
  width: 18%;
  border: 1px solid #ccc;
  padding: 10px;

  ul {
    padding-left: 20px;
    margin-top: 5px;
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
  }

  li {
    list-style-type: none;
    font-size: 17px;
    border: 1px solid #333;
    border-radius: 2px;
    padding: 3px;
  }
}

</style>
