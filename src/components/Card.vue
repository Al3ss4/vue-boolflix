  <template>
  <div class="card">
    <ul>
      <li>Titolo: {{ features.title }}</li>
      <li>Titolo originale: {{ features.original_title }}</li>
      <li>Lingua: {{ features.original_language }}</li>
      <li>Voto: {{ features.vote_average }}</li>
    </ul>
  </div>
</template>
<script>
export default {
  name: "CardComponent",
  props: ["features"],
};
</script>
<style lang="scss" scoped>

 ul{
    margin-top: 10px;
    li{
      list-style: none;
    }
 }
</style>