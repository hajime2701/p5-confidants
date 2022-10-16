<template>
  <div class="main-contents">
    <b-row>
      <b-col
        v-for="confidant in confidants"
        :key="confidant.index"
        cols="2"
        class="d-flex justify-content-center card-col"
      >
        <nuxt-link :to="'/confidants/' + confidant.index">
          <img :src="'img/' + confidant.name + '.jpg'" />
        </nuxt-link>
      </b-col>
    </b-row>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import data from '~/static/json/confidant_data.json'

export default Vue.extend({
  data() {
    const confidantsData: { name: any; index: number }[] = []

    data.forEach(function (x: any, i: number) {
      confidantsData.push({
        name: x.confidant,
        index: i + 1,
      })
    })

    return {
      confidants: confidantsData,
    }
  },

  head() {
    return {
      title: 'Home',
    }
  },
})
</script>

<style>
.card-col {
  padding: 5px;
}
.main-contents {
  padding-left: 3%;
  padding-right: 3%;
}
</style>
