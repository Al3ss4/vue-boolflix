  <template>
  <div class="card-cont m-2">
    <div class="poster">
      <div v-if="coverImg.includes(null)">
        <img class="poster-img"
          :src="require(`../assets/${undefined}.png`)"
          :alt="features.original_language"
        />
      </div>
      <div v-else>
        <img :src="coverImg" :alt="features.title" />
      </div>
    </div>
    <div class="film-info">
      <p>
        <span class="fw-bold">Titolo:</span>
        {{ features.title || features.name }}
      </p>

      <p>
        <span class="fw-bold">Titolo originale:</span>
        {{ features.original_title || features.original_name }}
      </p>

      <p v-if="flags.includes(features.original_language)">
        <span class="fw-bold">Lingua</span>
        <img
          class="flag"
          :src="require(`../assets/${features.original_language}.png`)"
          alt="features.original_language"
        />
      </p>
      <p v-else>
        <span class="fw-bold">Lingua</span>

        <img
          class="flag"
          :src="require(`../assets/${undefined}.png`)"
          :alt="features.original_language"
        />
      </p>
      <div class="d-flex">
        <span class="fw-bold me-2">Voto:</span>
        <p v-for="(star, i) in stars" :key="i" class="star">
          <i class="fas fa-star"></i>
        </p>
      </div>
      <p>
        <strong>Overview: </strong>
        <span class="over-view" v-if="features.original_title">{{
          features.overview
        }}</span>
        <span class="over-view" v-else>{{ features.original_name }}</span>
      </p>
    </div>
  </div>
</template>
<script>
export default {
  name: "CardComponent",
  props: {
    features: {
      type: [Array, Object],
    },
    img: String,
    vote: Number,
  },
  data() {
    return {
      flags: ["it", "fr", "es", "de", "ja", "en"],
      coverImg: "",
      stars: 0,
    };
  },
  created() {
    this.addPoster();
    this.voteStar();
  },
  methods: {
    addPoster() {
      this.coverImg = "https://image.tmdb.org/t/p/" + "w200" + this.img;
    },
    voteStar() {
      if (parseInt(this.vote) != 0) {
        this.stars = Math.round(parseInt(this.vote) / 2);
      } else {
        this.stars = null;
      }
    },
  },
};
</script>
<style lang="scss" scoped>
.card-cont {
  height: 25%;
  position: relative;
}
.film-info {
  position: absolute;
  top: 0;
  display: none;
  padding: 20px;
  background-color: black;
  width: 100%;
  z-index: 999;
    overflow-y:scroll;
  overflow-x: hidden;
}

.card-cont:hover .film-info {
  display: block;
   height: 95%;
 
}
p {
  color: white;
  img {
    width: 8%;
  }
  .flag {
    width: 15%;
    margin: 10px;
  }
  i {
    color: yellow;
  }
}

.poster {
 
  img {
    width: 100%;
  }
  .poster-img{
  width: 200px;
  height: 200px;
  
}
}
.yellow {
  color: yellow;
}
</style>