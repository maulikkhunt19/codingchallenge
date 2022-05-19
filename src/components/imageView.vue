<template>
  <div class="gallery">
    <div class="gallery-panel" v-for="item in imageData" :key="item.id">
      <div class="border">
        <img
          v-bind:src="`https://picsum.photos/id/${item.id}/500/600.jpg`"
          alt=""
          class="image"
        />
        <div class="image-caption">
          <p class="author border">{{ item.author }}</p>
        </div>
      </div>
    </div>
  </div>
</template>
<script lang="ts">
import { defineComponent } from "vue";
import axios from "axios";

export default defineComponent({
  name: "imageData",
  components: {},
  data() {
    return { imageData: undefined };
  },
  mounted() {
    axios
      .get(
        "https://picsum.photos/v2/list?page=" +
          (Math.floor(Math.random() * 50) + 1) +
          "&limit=12"
      )
      .then((resp) => {
        this.imageData = resp.data;
      });
  },
});
</script>

<style>
.gallery {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(20rem, 1fr));
  grid-gap: 2rem;
  max-width: 80rem;
  margin: 5rem auto;
}

.gallery-panel img {
  width: 100%;
  height: 35rem;
  object-fit: cover;
  border-radius: 0.75rem;
}
.author {
  text-align: center;
  color: #7a7c7f;
  font-family: "Libre Baskerville", serif;
  font-size: 28px;
}
</style>
