<template>
  <div>
    <b-navbar sticky="true" variant="dark" class="confidant-nav">
      <b-navbar-brand>
        <h1 class="confidant-name">{{ name }}</h1>
      </b-navbar-brand>
    </b-navbar>

    <b-container class="main-contents">
      <b-row class="justify-content-center">
        <h2 class="entry-header">Benefits</h2>
        <b-table
          :fields="benefitFields"
          :items="benefitItems"
          table-variant="dark"
          bordered="true"
        >
        </b-table>
      </b-row>

      <b-row
        v-for="entry in entryItems"
        :key="entry.header"
        class="justify-content-center"
      >
        <b-table-simple borderless="true">
          <b-tr>
            <b-td class="text-center">
              <h2 class="entry-header">{{ entry.header }}</h2>
            </b-td>
          </b-tr>
          <b-tr v-if="entry.sub">
            <b-td class="text-center">
              <h4 class="entry-header">{{ entry.sub }}</h4>
            </b-td>
          </b-tr>
        </b-table-simple>
        <b-table
          :fields="entryFields"
          :items="entry.contents"
          thead-tr-class="d-none"
          table-variant="dark"
          bordered="true"
        ></b-table>
      </b-row>
    </b-container>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import data from '~/static/json/confidant_data.json'

export default Vue.extend({
  data() {
    const index: number = parseInt(this.$route.params.id)
    const confidantData = data[index - 1]
    const bFields = [
      { key: 'Rank', tdClass: 'b-rank' },
      { key: 'Ability' },
      { key: 'Description' },
    ]
    const bItems: { Rank: string; Ability: string; Description: string }[] = []

    confidantData.data[0].entries.slice(1).forEach(function (x: any[]) {
      const item = {
        Rank: x[0],
        Ability: x[1],
        Description: x[2],
      }
      bItems.push(item)
    })

    const entries: {
      header: string
      sub: string
      contents: { label: string; resp1: string; resp2: string; resp3: string }[]
    }[] = []

    const eFields = [
      { key: 'label', tdClass: 'b-rank' },
      { key: 'resp1' },
      { key: 'resp2' },
      { key: 'resp3' },
    ]

    confidantData.data.slice(1).forEach(function (x) {
      const eItems: {
        label: string
        resp1: string
        resp2: string
        resp3: string
      }[] = []

      x.entries.forEach(function (y: string | any[]) {
        eItems.push({
          label: y[0],
          resp1: y[1],
          resp2: y[2],
          resp3: y.length === 4 ? y[3] : '',
        })
      })

      entries.push({
        header: x.header,
        sub: x.sub,
        contents: eItems,
      })
    })

    return {
      name: confidantData.confidant,
      benefitFields: bFields,
      benefitItems: bItems,
      entryFields: eFields,
      entryItems: entries,
    }
  },

  head() {
    const index: number = parseInt(this.$route.params.id)
    const confidantData = data[index - 1]

    return {
      title: confidantData.confidant,
    }
  },
})
</script>

<style>
.main-contents {
  padding-top: 3%;
  padding-left: 3%;
  padding-right: 3%;
}

.entry-header {
  align-content: center;
  color: white;
}

.b-rank {
  font-weight: bold;
}

.confidant-nav {
  border-bottom: 1px solid white;
}

.confidant-name {
  color: white !important;
}
</style>
