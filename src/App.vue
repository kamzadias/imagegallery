<template>
  <div id="app">
    <div class="filter-section">
      <input
        v-model="filterKey"
        type="text"
        placeholder="Фильтр по названию или автору"
      />
    </div>

    <image-list
      v-if="!selectedImage"
      :images="filteredImages"
      @select="showImage"
    ></image-list>
    <image-viewer
      v-else
      :image="selectedImage"
      @close="selectedImage = null"
    ></image-viewer>
  </div>
</template>

<script>
import ImageList from "./components/ImageList.vue";
import ImageViewer from "./components/ImageViewer.vue";

export default {
  name: "App",
  components: {
    ImageList,
    ImageViewer,
  },
  data() {
    return {
      selectedImage: null,
      filterKey: "",
      images: [
        {
          id: 1,
          url: "https://images.unsplash.com/photo-1698156366381-4115aaf41f7f?auto=format&fit=crop&q=80&w=3516&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
          title: "Моржи",
          author: "Иван Ургант",
        },
        {
          id: 2,
          url: "https://images.unsplash.com/photo-1697977411753-96fd0d452169?auto=format&fit=crop&q=80&w=3540&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
          title: "Красное Облако",
          author: "Артур Пиражков",
        },
        {
          id: 3,
          url: "https://images.unsplash.com/photo-1682685797277-f2bf89b24017?auto=format&fit=crop&q=80&w=3540&ixlib=rb-4.0.3&ixid=M3wxMjA3fDF8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
          title: "Пещера",
          author: "Анна Федоровна",
        },
      ],
    };
  },
  methods: {
    showImage(image) {
      this.selectedImage = image;
    },
  },
  computed: {
    filteredImages() {
      return this.images.filter((image) => {
        return (
          image.title.toLowerCase().includes(this.filterKey.toLowerCase()) ||
          image.author.toLowerCase().includes(this.filterKey.toLowerCase())
        );
      });
    },
  },
};
</script>

<style>
.filter-section {
  margin-bottom: 20px;
}

.filter-section input {
  padding: 10px;
  width: 300px;
  border-radius: 5px;
  border: 1px solid #ccc;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
