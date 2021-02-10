<template>
  <div id="app">
    <nav class="nav">
      <img class="logo" src="@/assets/logo.svg" alt="LiveWall">
      <div class="link-holder">
        <router-link to="/">Deelnemers</router-link>
        <router-link to="/upload">Upload</router-link>
      </div>
    </nav>
    <div class="background-texture"></div>
    <router-view/>
  </div>
</template>

<style lang="scss" scoped>
  .nav {
    display:flex;
    padding: absolute;
    top:0;
    left:0;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
    background-color: rgba(255,165,0,1);
    padding: 10px 20px;
    .logo {
      width:25px;
    }
    .link-holder {
      a {
        font-size: 16px;
        color:black;
        text-decoration: none;
        margin-right: 14px;
        text-transform: uppercase;
        &:last-child {
          margin: 0;
        }
        &:hover {
          text-decoration: underline;
        }
      }
    }
  }

  .background-texture {
    height: 200px;
    width:100%;
    background-image: url('./assets/background.jpg');
    background-size: cover;
    background-position: center;
  }
</style>
