<template>
  <div>
    <b-container fluid class="vh-100">
      <b-row class="vh-100">
        <b-col cols="2" class="fixed-sidebar">
          <b-nav vertical>
            <b-nav-item class="side-nav-item" to="/"><b>Home</b></b-nav-item>
            <b-nav-item class="side-nav-item" to="/confidants/1">Chariot (Ryuji Sakamoto)</b-nav-item>
            <b-nav-item class="side-nav-item" to="/confidants/2">Death (Tae Takemi)</b-nav-item>
            <b-nav-item class="side-nav-item" to="/confidants/3">Devil (Ichiko Ohya)</b-nav-item>
            <b-nav-item class="side-nav-item" to="/confidants/4"
              >Emperor (Yusuke Kitagawa)</b-nav-item
            >
            <b-nav-item class="side-nav-item" to="/confidants/5">Empress (Haru Okumura)</b-nav-item>
            <b-nav-item class="side-nav-item" to="/confidants/6">Fortune (Chihaya Mifune)</b-nav-item>
            <b-nav-item class="side-nav-item" to="/confidants/7">Hanged (Munehisa Iwai)</b-nav-item>
            <b-nav-item class="side-nav-item" to="/confidants/8">Hermit (Futaba Sakura)</b-nav-item>
            <b-nav-item class="side-nav-item" to="/confidants/9"
              >Hierophant (Sojiro Sakura)</b-nav-item
            >
            <b-nav-item class="side-nav-item" to="/confidants/10">Lovers (Ann Takamaki)</b-nav-item>
            <b-nav-item class="side-nav-item" to="/confidants/11">Moon (Yuuki Mishima)</b-nav-item>
            <b-nav-item class="side-nav-item" to="/confidants/12"
              >Priestess (Makoto Niijima)</b-nav-item
            >
            <b-nav-item class="side-nav-item" to="/confidants/13">Star (Hifumi Togo)</b-nav-item>
            <b-nav-item class="side-nav-item" to="/confidants/14"
              >Sun (Toranosuke Yoshida)</b-nav-item
            >
            <b-nav-item class="side-nav-item" to="/confidants/15"
              >Temperance (Sadayo Kawakami)</b-nav-item
            >
            <b-nav-item class="side-nav-item" to="/confidants/16">Tower (Shinya Oda)</b-nav-item>
          </b-nav>
        </b-col>
        <b-col cols="10" style="padding: 0px">
          <div class="vh-100 contents">
            <Nuxt />
          </div>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<style>
.contents {
  max-height: 100%;
  overflow-y: scroll;
  background-color: #343a40;
  color: white;
}

.main-nav {
  background-color: #212529;
}

.fixed-sidebar {
  background-color: #212529;
  height: 100%;
  padding-right: 0px;
  padding-left: 0px;
  overflow-y: scroll;
}

.side-nav-item {
  border-top: 1px solid black;
  border-bottom: 1px solid black;
}

.nav-link,
.nav-link:hover {
  color: white;
}

.side-nav-item:hover {
  background-color: #495057;
}
</style>
