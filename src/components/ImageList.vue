<template>
  <div class="image-list">
    <div
      v-for="image in images"
      :key="image.id"
      class="image-item"
      @click="selectImage(image)"
    >
      <img :src="image.url" :alt="image.title" />
      <p>{{ image.title }}</p>
      <p>Автор: {{ image.author }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "ImageList",
  props: {
    images: {
      type: Array,
      default: () => [],
    },
  },
  methods: {
    selectImage(image) {
      this.$emit("select", image);
    },
  },
};
</script>

<style scoped>
.image-list {
  display: flex;
  flex-wrap: wrap;
  gap: 16px;
  justify-content: center;
}

.image-item {
  background-color: #f9f9f9;
  border: 1px solid #ddd;
  border-radius: 8px;
  overflow: hidden;
  cursor: pointer;
  width: 200px;
  transition: transform 0.2s ease-in-out;
}

.image-item:hover {
  transform: scale(1.05);
}

.image-item img {
  max-width: 100%;
  height: auto;
}

.image-item p {
  padding: 4px;
  margin: 0;
  text-align: center;
}
</style>
