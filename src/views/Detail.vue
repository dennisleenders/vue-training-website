<template>
  <div class="detail">
    <section class="participant">
      <router-link to="/">TERUG</router-link>
      <div class="text large yellow">DEELNEMER DETAILS</div>
      <div class="participant-details">
        <div class="information">
          <div class="name">
            <div class="text">NAAM</div>
            <div class="text">{{ participant.naam}}</div>
          </div>
          <div class="department">
            <div class="text">AFDELING</div>
            <div class="text">{{ participant.afdeling}}</div>
          </div>
          <div class="introduction">
            <div class="text">PERSOONLIJKE TEKST</div>
            <div class="text">{{ participant.tekst}}</div>
          </div>
        </div>
        <img class="participant-image" :src=participant.img>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: 'Detail',
  data(){
    return {
      participant: {}
    }
  },
  created(){
    this.getData();
  },
  methods: {
    getData(){
      this.axios.post('http://dump.lwdev.nl/vue-cursus-api/deelnemerDetails/', {id: this.$route.params.id }).then((response) => {
        this.participant = response.data
      })   
    }
  }  
}
</script>

<style lang="scss" scoped>
  .participant {
    position: relative;
    max-width: 800px;
    background:white;
    margin:0 auto;
    padding:36px;
    transform:translate(0, -60px);
    .participant-details {
      display: flex;

    }
  }
</style>
