<template>
  <div class="gallery">
    <div class="gallery-panel" v-for="item in imageData" :key="item.id">
      <img
        v-bind:src="`https://picsum.photos/id/${item.id}/500/600.jpg`"
        alt=""
        class="image"
      />
      <div class="image-caption">
        <p class="author">{{ item.author }}</p>
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
    axios.get("https://picsum.photos/v2/list?page=2&limit=12").then((resp) => {
      this.imageData = resp.data;
      console.log(resp.data);
    });
  },
  computed: {
    imageWithId(id: string) {
      console.log("https://picsum.photos/id/" + id + "/200/300.jpg");
      return "hello";
    },
  },
});
</script>

<style>
.gallery {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(20rem, 1fr));
  grid-gap: 1rem;
  max-width: 80rem;

  margin: 5rem auto;
  /* padding: 0 5rem; */
}

.gallery-panel img {
  width: 100%;
  height: 35rem;
  object-fit: cover;
  border-radius: 0.75rem;
  text-align: center;
}
.author {
  text-align: center;
  color: #7a7c7f;
  font-family: "Libre Baskerville", serif;
  font-size: 28px;
}
</style>
