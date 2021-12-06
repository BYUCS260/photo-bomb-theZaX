<template>
  <div class="photo-page" v-if="photo">
    <div class="photo-page__container">
      <div class="photo-page__image-container">
        <img class="photo-page__image" :src="photo.path" alt="" />
      </div>
      <div class="photo-page__info-container">
        <div class="photo-page__info">
          <div class="photo-page__info-title">{{ photo.title }}</div>
          <div class="photo-page__info-description">
            {{ photo.description }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "PhotoPage",

  data() {
    return {
      photo: {
        path: "link",
        title: "sdfsadf",
        description: "asdf",
      },
    };
  },
  created() {
    this.fetchPhoto();
  },

  methods: {
    async fetchPhoto() {
      const id = this.$route.params.id;
      const url = `/api/photos/photo/${id}`;
      const response = await axios.get(url);

      this.photo = response.data;
    },
  },
};
</script>


<style>
.photo-page {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.photo-page__container {
  margin-top: 120px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.photo-page__image-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.photo-page__image {
  width: 100%;
  height: auto;
}

.photo-page__info-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.photo-page__info {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.photo-page__info-title {
  font-size: 1.5em;
}

.photo-page__info-description {
  font-size: 1em;
}

.photo-page__info-buttons {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
}

.photo-page__info-button {
  margin: 0 0.5em;
}
</style>



