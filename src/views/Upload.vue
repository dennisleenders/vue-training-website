<template>
  <div class="upload">
    <div class="upload-card">
      <router-link to="/">TERUG</router-link>
      <div class="text large yellow">UPLOAD FOTO</div>
      <div class="text">Voeg nieuwe foto toe</div>
      <vue-dropzone id="drop1" :options="dropOptions"></vue-dropzone>
    </div>
  </div>
</template>

<script>
import vueDropzone from "vue2-dropzone";

export default {
  name: 'Upload',
  data: () => ({
    dropOptions: {
      url: "https://httpbin.org/post"
    }
  }),  
  components: {
    vueDropzone
  }  
}
</script>

<style lang="scss" scoped>
  .upload-card {
    position: relative;
    max-width: 800px;
    background:white;
    margin:0 auto;
    padding:36px;
    transform:translate(0, -60px);
    
    .vue-dropzone {
      display: flex;
      align-items: center;
      justify-content: center;
      width:100%;
      height:100px;
      border:1px solid rgba($color: #000000, $alpha: 0.8);
      
      .dz-message {
        text-transform: uppercase;
      }

      .dz-preview {
        display:flex;
        flex-direction: row;
        align-items: center;
        margin-left: 18px;
      }
    }
  }
</style>
