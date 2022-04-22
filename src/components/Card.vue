  <template>
  <div class="card">
    <ul>
      <li>
        <img :src="coverImg" :alt="features.title" />
      </li>
      <li>Titolo:  {{features.title || features.name}}</li>
      <li>Titolo originale: {{ features.original_title || features.original_name }}</li>
      <li v-if="flags.includes(features.original_language)">
        <span>Lingua</span>
        <img
          class="flag"
          :src="require(`../assets/${features.original_language}.png`)"
          alt="features.original_language"
        />
      </li>
      <li v-else>
        <span class="fw-bold">Lingua</span>

        <img
          class="flag"
          :src="require(`../assets/${undefined}.png`)"
          :alt="features.original_language"
        />
      </li>
         <ul class="d-flex">
                <span class="fw-bold me-2">Voto:</span> 
                <li v-for="(star, i) in stars" :key="i" class="star" >
                    <i class="fas fa-star"></i>
                </li> 
          </ul>
    </ul>
  </div>
</template>
<script>
export default {
  name: "CardComponent",
  props: {
    features: {
    type: [ Array, Object ]
  },
    img : String,
    vote: Number,
  },
  data() {
    return {
      flags: ["it", "fr", "es", "de", "ja", "en", "undefined"],
      coverImg: "",
      stars:0,
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
    voteStar(){
        if (parseInt(this.vote) != 0){
        this.stars = Math.round(parseInt(this.vote) / 2);
      } else {this.stars = null}
      }
    
  },
};
</script>
<style lang="scss" scoped>
ul {
  margin-top: 10px;
  li {
    list-style: none;
    

      .flag {
        width: 2%;
        margin: 2px;
      }
    
  }
    .star{
        color: yellow;
      }
    
}
</style>