<template>
  <div id="app">
    <div class="container grid-lg">
      <header class="navbar">
        <section class="navbar-section">
          <router-link to="/" class="btn btn-link">Home</router-link>
          <router-link to="/" class="btn btn-link">kanban</router-link>
        </section>
        <section class="navbar-center">
          <img
            class="img-responsive img-logo"
            src="../src/assets/logo.png"
            alt="Logo da Switch Case"
          />
          <section class="navbar-section">
            <a href="" class="btn btn-link">Twitter</a>
            <a href="" class="btn btn-link">GitHub</a>
          </section>
        </section>
      </header>
      <router-view class="pt-2"></router-view>
    </div>
  </div>
</template>

<style scoped>
.img-logo {
  max-width: 100px;
}
</style>
