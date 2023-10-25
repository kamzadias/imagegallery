<template>
  <div class="image-viewer" @click="closeViewer">
    <img :src="image.url" :alt="image.title" />

    <div class="info">
      <p class="title">{{ image.title }}</p>

      <p class="author">Автор: {{ image.author }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "ImageViewer",
  props: {
    image: Object,
  },
  methods: {
    closeViewer() {
      this.$emit("close");
    },
  },
};
</script>

<style scoped>
.image-viewer {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: rgba(0, 0, 0, 0.5);
  cursor: zoom-out;
  z-index: 1000;
}

.image-viewer img {
  max-width: 90%;
  max-height: 90%;
  border-radius: 8px;
  box-shadow: 0 12px 15px 5px rgba(0, 0, 0, 0.3);
}

.image-viewer p {
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  color: white;
  text-align: center;
  font-size: larger;
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.5);
}
.image-viewer .title {
  bottom: 13%;
}

.image-viewer .author {
  bottom: 10%;
}
</style>
