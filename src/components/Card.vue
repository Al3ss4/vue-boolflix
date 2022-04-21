  <template>
  <div class="card">
    <ul>
      <li>Titolo: {{ features.title }}</li>
      <li>Titolo originale: {{ features.original_title }}</li>
      <li v-if="flags.includes(features.original_language)">
        <span>Lingua</span>
        <img
          :src="require(`../assets/${features.original_language}.png`)"
          alt="features.original_language"
        />
      </li>
      <li v-else>
        <span class="fw-bold">Lingua</span>

        <img
          :src="require(`../assets/${undefined}.png`)"
          :alt="features.original_language"
        />
      </li>
      <li>Voto: {{ features.vote_average }}</li>
    </ul>
  </div>
</template>
<script>
export default {
  name: "CardComponent",
  props: ["features"],
  data() {
    return {
      flags: ["it", "fr", "es", "de", "ja", "en", "undefined"],
    };
  },
};
</script>
<style lang="scss" scoped>
ul {
  margin-top: 10px;
  li {
    list-style: none;
    img{
      width: 2%;
      margin: 2px;
    }
  }
}
</style>