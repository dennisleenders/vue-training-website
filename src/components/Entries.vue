<template>
  <div class="entries">
    <div class="entry" v-for="entry in data" :key="entry.id" @click="$emit('toDetail', entry)">
      <div class="line"></div>
      <div class="details">
        <div class="name">{{ entry.naam }}</div>
        <div class="department">{{ entry.afdeling }}</div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'Entry',
    props: {
      data: Array
    }
  }
</script>

<style lang="scss" scoped>
  .entry {
    display:flex;
    position:relative;
    flex-direction: row;
    align-items: center;
    background-color: white;
    border:1px solid orange;
    padding:12px 12px 28px;
    margin-bottom: 24px;
    box-shadow: 0px 0px 5px rgba($color: #000000, $alpha: 0.2);
    transition:box-shadow .4s ease-out;
    cursor:pointer;
    &:hover {
      box-shadow: 0px 0px 8px rgba($color: #000000, $alpha: 0.3);
    }
    &:before {
      content:'';
      position:absolute;
      top:0;
      left:0;
      height:100%;
      width:4px;
      background:orange;
    }
    .details {
      .name {
        font-size: 18px;
        margin-bottom: 4px;
      }
      .department {
        font-size: 16px;
      }
    }
  }
</style>