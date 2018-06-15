<template>
  <section class="container">
    <template v-if="dday > 0">
      <div>D-{{ dday }}</div>
    </template>
    <template v-else-if="dday === 0">
      <div>D-Day!!!!!</div>
    </template>
    <template v-else>
      <div>지남.</div>
    </template>


    <div v-for="meet in meets" :key="meet.date">
      <div v-html="meet.contents"></div>
      <div v-for="user in meet.users" :key="user.id">
        {{ user }}
      </div>
    </div>
  </section>
</template>
<script>

import * as moment from "moment"
import "moment-timezone"

const meets = require("~/assets/json/meets.json").meets

const NEXT_DODO_DATE = moment.tz("2018-06-18 19:30:00", "Asia/Seoul")

export default {
  components: {
  },
  data() {
    return {
      meets,
      dday: null,
    }
  },
  mounted() {
    this.calculateDday()
  },
  methods: {
    calculateDday() {
      this.dday = NEXT_DODO_DATE.diff(new Date(), "days")
    }
  }
}
</script>
