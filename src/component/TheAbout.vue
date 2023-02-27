<template>
    <div class="about">
      <div class="about_text has-text-centered">
						A magical new way to interact <br>
            with iPhone. Groundbreaking <br>
            safety features designed to save <br>
            lives. An innovative 48MP camera <br>
            for mind-blowing detail. All <br>
            powered by the ultimate smartphone chip.
      </div>
      <div class="image-list-container">
        <div class="image-container">
          <img :src="getImageUrl()" alt="Image" />
        </div>
        <div class="items-list">
          <ul>
            <li v-for="(item, index) in items" :key="index" @click="changeImage(index)" :class="{ 'active': activeIndex === index }">
              {{ item }}
            </li>
          </ul>
        </div>
        </div>
    </div>
</template>

<style lang="scss" scoped>
.about {
    min-height: 100vh;
}

.about_text {
  font-size: 24px;
  background: linear-gradient(180deg,#ffb6ff,#b344ff);
  text-transform: uppercase;
  -webkit-text-fill-color: transparent;
  -webkit-background-clip: text;
  overflow: hidden;
}
.image-list-container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.image-container {
  margin-right: 20px;
}

.items-list {
  flex-grow: 1;
}
.active {
  color: white;
}
</style>

<script>
export default {
  data() {
    return {
      items: ['Deep Purle', 'Gold', 'Silver', 'Space Black'],
      activeIndex: 0,
    };
  },
  methods: {
    changeImage(index) {
      this.activeIndex = index;
    },
    getImageUrl() {
      const images = ['/src/assets/gallery_deep_purple.png', '/src/assets/gallery_gold.png', '/src/assets/gallery_silver.png', '/src/assets/gallery_space_black.png'];
      return images[this.activeIndex];
    },
  },
};
</script>
