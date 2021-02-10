<template>
  <!-- Waarom kan ik hier geen <page> tag gebruiken html5 sementics, vue gaat erom zeuren-->
  <div class="home">
    <section class="participants">
      <div class="filter">
        <div class="text large yellow">ZOEK DEELNEMER</div>
        <input type="text" v-model="searchInput">
      </div>
      <div class="list">
        <Entries v-bind:data="filteredEntries" @toDetail="toDetail"/>
      </div>
    </section>
  </div>
</template>

<script>
import Entries from '@/components/Entries.vue'

export default {
  name: 'Home',
  components: {
    Entries
  },  
  data(){
    return {
      entries: [],
      searchInput: ''
    }
  },  
  created(){
    this.getData();
  },  
  computed:{
    filteredEntries(){
      const search = this.searchInput.toLowerCase().trim();
      if(!search){ return this.entries; }
      return this.entries.filter( entry => entry.naam.toLowerCase().indexOf(search) > -1);
    }
  },  
  methods: {
    getData(){
      this.axios.get('http://dump.lwdev.nl/vue-cursus-api/deelnemers/').then((response) => {
        this.entries = response.data
      })   
    },
    toDetail(data){
      this.$router.push({ name: 'Detail', params: { id: data.id } })
    }
  }  
}
</script>

<style lang="scss" scoped>
  .participants {
    position: relative;
    max-width: 600px;
    background:white;
    margin:0 auto;
    padding:36px;
    transform:translate(0, -60px);
    .filter {
      margin-bottom: 24px;
      .text {
        font-size: 18px;
        color:orange;
        margin-bottom: 8px;
      }
      input {
        font-family: "Roboto Condensed";
        box-sizing: border-box;
        width:100%;
        padding:12px;
        outline: 0;
        border:1px solid rgba($color: #000000, $alpha: 0.2)
      }
    }
  }
</style>
