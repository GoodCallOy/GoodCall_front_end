<template>
  <button
    :class="['menu-button', { active: isActive }]"
    @click="handleClick">
    <span>{{ label }}</span>
  </button>
</template>

<script>
export default {
  props: {
    // Is this button currently active?
    isActive: {
      type: Boolean,
      default: false,
    },
    label: {
      type: String,
      required: true,
    }
  },
  methods: {
    handleClick() {
      // Emit event when button is clicked
      this.$emit('button-click', this.label);
    }
  }
};
</script>

<style scoped>
.menu-button {
  background-color: white;
  color: black;
  border: none;
  padding: 10px;
  width: 100%;
  text-align: center;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.menu-button:hover {
  background-color: gray;
}

.menu-button.active {
  background-color: lightgray; /* Active button color */
}

.menu-button:focus {
  outline: none;
}
</style>
