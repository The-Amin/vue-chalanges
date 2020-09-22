<template>
  <div class="container">
    <SearchBar @newSearch="newSearch"></SearchBar>
    <div class="row">
      <VideoDetail :video="selectedVideo"></VideoDetail>
      <VideoList :videos="videos" @videoSelect="onVideoSelect"></VideoList>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import SearchBar from './components/SearchBar';
import VideoList from './components/VideoList';
import VideoDetail from './components/VideoDetail';

const API_KEY = 'AIzaSyBZKgU-dAd1sAFIjfFqP96kzoWdm75RmNI';

export default {
  name: 'App',
  components: {
    SearchBar,
    VideoList,
    VideoDetail
  },
  data() {
    return { videos: null, selectedVideo: null };
  },
  methods: {
    newSearch(searchValue) {
      axios
        .get('https://www.googleapis.com/youtube/v3/search', {
          params: {
            key: API_KEY,
            type: 'video',
            part: 'snippet',
            q: searchValue
          }
        })
        .then(response => (this.videos = response.data.items));
    },
    onVideoSelect(video) {
      this.selectedVideo = video;
    }
  }
};
</script>
