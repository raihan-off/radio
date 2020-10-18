<template>
  <div class="home">
    <img :src="require('../assets/label.png')" />
    <div class="konten">
      <h1>Playing</h1>
      <h2 class="song-title">{{ current.title }} - {{ current.artist }}</h2>
      <div class="action">
        <v-btn id="prev" class="prev" @click="prev">prev</v-btn>
        <v-btn id="play" class="play" v-if="!isPlaying" @click="play">Play</v-btn>
        <v-btn id="stop" class="pause" v-else @click="pause">Pause</v-btn>
        <v-btn id="next" class="next" @click="next">next</v-btn>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import Beranda from "@/components/Beranda.vue";

export default {
  name: "Home",
  components: {
    // eslint-disable-next-line vue/no-unused-components
    Beranda,
  },
  data() {
    return {
      current: {},
      index: 0,
      isPlaying: false,
      songs: [
        {
          title: "Ikigai",
          artist: "Idealism",
          src: require("../assets/idealism-ikigai.mp3"),
        },
        {
          title: "Snowman",
          artist: "WYS",
          src: require("../assets/wys-snowman.mp3"),
        },
      ],
      player: new Audio(),
    };
  },
  methods: {
    play(song) {
      if (typeof song.src != "undefined") {
        this.current = song;

        this.player.src = this.current.src;
      }

      this.player.play();
      this.isPlaying = true;
    },

    pause() {
      this.player.pause();
      this.isPlaying = false;
    },

    next() {
      this.index++;
      if (this.index > this.songs.length - 1) {
        this.index = 0;
      }
      this.current = this.songs[this.index];
      this.play(this.current);
    },

    prev() {
      this.index--;
      if (this.index < 0) {
        this.index = this.songs.length - 1;
      }
      this.current = this.songs[this.index];
      this.play(this.current);
    },
  },

  created() {
    this.current = this.songs[this.index];
    this.player.src = this.current.src;
  },
};
</script>

<style scoped>
.konten {
  padding: 40px 0px 0px 0px;
}

h1,
h2 {
  color: white;
}

.action {
  margin: 10% 0% 0% 25%;
  height: 20%;
  width: 50%;
}

#stop {
  margin: 0% 5% 0% 5%;
}

#play {
  margin: 0% 5% 0% 5%;
}

#like {
  margin: 0% 5% 0% 5%;
}

button {
  appearance: none;
  background: none;
  border: none;
  outline: none;
  cursor: pointer;
}

.play,
.pause {
  font-size: 20px;
  font-weight: 700;
  padding: 15px 25px;
  border-radius: 8px;
  color: black;
  background-color: white;
  cursor: pointer;
}

.next,
.prev {
  font-size: 15px;
  font-weight: 500;
  padding: 15px 25px;
  border-radius: 8px;
  color: black;
  background-color: white;
  cursor: pointer;
}
</style>
