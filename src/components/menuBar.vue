<template>
  <h3>Menu</h3>
  <div class="menu">
    <menuBarItem
      v-for="item in menuItems"
      :key="item.label"
      :label="item.label"
      :isActive="item.label === activeItem"
      @button-click="handleButtonClick"
    />
  </div>
</template>

<script>
import menuBarItem from './menuBarItem.vue';

export default {
  components: {
    menuBarItem,
  },
  data() {
    return {
      activeItem: 'DashBoard',
      menuItems: [
        { label: 'DashBoard' },
        { label: 'Cases' },
        { label: 'Agents' },
        { label: 'About' },
      ],
    };
  },
  methods: {
    handleButtonClick(label) {
      this.activeItem = label;
      // Emit an event to the parent component
      this.$emit('menu-item-click', label);
    },
  },
};
</script>

<style scoped>
.menu {
  display: flex;
  flex-direction: column;
  width: 200px;
  padding: 10px;
}

h3 {
  text-align: center;
  color: rgb(11, 6, 6);
}
</style>
