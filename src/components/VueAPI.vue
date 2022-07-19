<template>
  <div>
    <div v-for="photo in photos" v-bind:key="photo.id">
      <h3>Photo title: {{ photo.title }}</h3>
      <p>Photo url: {{ photo.url }}</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      photos: [],
    };
  },

  methods: {
    async getData() {
      try {
        const response = await this.axios.get(
          "https://jsonplaceholder.typicode.com/photos"
        );
		console.log(response.data);
        this.photos = response.data;
      } catch (error) {
        console.log(error);
      }
    },
  },

  created() {
    this.getData();
  },
};
</script>