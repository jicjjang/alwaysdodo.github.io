<template>
  <div>

    <div class="section section-header en">
      <div class="container">
        <div class="logo"></div>

        <!-- <a class="button button-text">참가신청</a> -->
        <a class="button button-icon" href="mailto:we.are.dodo.2018@gmail.com"></a>
      </div>
    </div>

    <div class="section section-intro">
      <div class="container">
        <div class="title en">Until next DODO</div>
        <div class="d-day-container en">
          <div class="d-day" v-if="!hasNext">없음.</div>
          <div class="d-day" v-else-if="dday !== null">D-{{ dday }}</div>
          <div class="d-day" v-else-if="dday === 0">D-{{ dday }}</div>
          <div class="d-day" v-else>지.남</div>
        </div>
        <div class="description en">DO <span class="span">What you want to</span> DO</div>
        <div class="buttons">
          <a class="button button-slack en" href="https://www.slack.com" target="blank">Slack</a>
          <a class="button button-gallery en" href="https://photos.app.goo.gl/HfCLGo3SB2F572yj6" target="blank">Gallery</a>
          <a class="button button-github en" href="https://github.com/we-are-dodo" target="blank">Github</a>
        </div>
      </div>
    </div>

    <div class="section-body">
      <div class="container">
        <div class="meets">
          <MeetItem v-for="(meet, index) in meets" :key="meet.date" :meet="meet" :opened="index === 0" />
        </div>
      </div>
    </div>
  </div>
</template>
<script>

import * as moment from "moment"
import "moment-timezone"
import MeetItem from "~/components/meet-item.vue"

const meets = require("~/assets/json/meets.json").meets

const NEXT_DODO_DATE = null // moment.tz("2018-06-18 19:30:00", "Asia/Seoul")

export default {
  components: {
    MeetItem,
  },
  data() {
    return {
      meets,
      dday: NEXT_DODO_DATE ? NEXT_DODO_DATE.diff(new Date(), "days") : null,
    }
  },
  mounted() {
    this.calculateDday()
  },
  computed: {
    hasNext() {
      return NEXT_DODO_DATE !== null
    },
  },
  methods: {
    calculateDday() {
      if (NEXT_DODO_DATE) {
        this.dday = NEXT_DODO_DATE.diff(new Date(), "days")
      }
    },
  }
}
</script>
