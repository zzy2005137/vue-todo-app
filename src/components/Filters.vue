<template>
  <div class="filters">
    <span
      v-for="filter in filters"
      :key="filter.label"
      class="filter"
      :class="{ active: filter.label === selectedLabel }"
      @click="$emit('changeFilter',filter.label)"
      >{{ filter.label }}
    </span>
  </div>
</template>

<script>
export default {
  name: "Filters",
  props: ["selectedLabel"],
  data() {
    return {
      filters: [{ label: "All" }, { label: "Left" }, { label: "Completed" }],
      // selectedId: "All",
    }
  },
  methods: {
    setSelected(label) {
      this.selectedId = label
    },
  },
}
</script>

<style scoped>
.filters {
  display: flex;
  margin: 1rem 1.2rem;
  color: #c0c2ce;
}

.filters span {
  margin-right: 1rem;
  transition: 0.5s;
  font-size: 1.2rem;
  cursor: pointer;
}

/* .filters span:active {
  color: #6b729c;
  transform: scale(1.2);
} */

.filter.active {
  color: #6b729c;
  transform: scale(1.15);
}
</style>
