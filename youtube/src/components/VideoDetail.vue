<template>
  <div v-if="video" class="col-md-8">
    <div class="embed-responsive embed-responsive-16by9">
      <iframe :src="videoUrl" frameborder="0"></iframe>
    </div>
    <div class="details">
      <h4>{{ video.snippet.title }}</h4>
      <p>{{ video.snippet.description }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'VideoDetail',
  props: ['video'],
  computed: {
    videoUrl() {
      var { videoId } = this.video.id;
      return `https://youtube.com/embed/${videoId} `;
    }
  },
  methods: {}
};
</script>

<style scoped>
.details {
  margin: 10px 0;
  padding: 10px;
  border: #ddd solid 1px;
  border-radius: 5px;
}
</style>
