<template>
  <div class="main-page">
    <div class="main-page__selected-items flex-row flex-btwn">
      <selected-items
        :title="'Left selected items:'"
        :selected-items="selectedUserItems"
        :counter="6"/>
      <selected-items
        :title="'Right selected items:'"
        :selected-items="selectedAvailableItem"/>
    </div>
    <div class="main-page__item-lists flex-row flex-btwn">
      <div class="left-block">
        <item-list
          title="Left Items:"
          :items="userItems"
          :maxSelect="6"
          @select="(item) => selectedUserItems = item"
        ></item-list>
      </div>
      <div class="right-block">
        <item-list
          title="Right Items:"
          :items="availableItems"
          :maxSelect="1"
          @select="(item) => selectedAvailableItem = item"
        ></item-list>
      </div>
    </div>
  </div>
</template>

<script>
import ItemList from '@/components/ItemList.vue';
import SelectedItems from '@/components/SelectedItems.vue';

export default {
  components: {
    ItemList,
    SelectedItems,
  },
  data() {
    return {
      userItems: [
        { id: 1, name: 'Shoes 1' },
        { id: 2, name: 'Shoes 2' },
        { id: 3, name: 'Shoes 3' },
        { id: 4, name: 'Shoes 4' },
        { id: 5, name: 'T-shirt 1' },
        { id: 6, name: 'T-shirt 2' },
        { id: 7, name: 'T-shirt 3' },
        { id: 8, name: 'T-shirt 4' },
      ],
      availableItems: [
        { id: 11, name: 'Jacket 1' },
        { id: 12, name: 'Jacket 2' },
        { id: 13, name: 'Jacket 3' },
        { id: 14, name: 'Jacket 4' },
        { id: 15, name: 'Hoodie 1' },
        { id: 16, name: 'Hoodie 2' },
        { id: 17, name: 'Hoodie 3' },
        { id: 18, name: 'Hoodie 4' },
      ],
      selectedUserItems: [],
      selectedAvailableItem: [],
    };
  },
};
</script>

<style lang="scss">
  .main-page {
    display: flex;
    flex-direction: column;
    max-width: 1440px;
    margin: 0 auto;
  }

  .flex-row {
    display: flex;
  }

  .flex-btwn {
    justify-content: space-between;
  }
</style>
