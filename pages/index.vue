<template>
  <div>

    <div class="section section-header en">
      <div class="container">
        <div class="logo"></div>

        <a class="button button-text">참가신청</a>
        <a class="button button-icon">??</a>
      </div>
    </div>

    <div class="section section-intro">
      <div class="container">
        <div class="title en">Until next DODO</div>
        <div class="d-day-container en">
          <div class="d-day" v-if="dday !== null">D-{{ dday }}</div>
          <div class="d-day" v-else-if="dday === 0">D-{{ dday }}</div>
          <div class="d-day" v-else>지.남</div>
        </div>
        <div class="description en">DO <span class="span">What you want to</span> DO</div>
        <div class="buttons">
          <a class="button button-slack en" href="https://www.slack.com" target="blank">Slack</a>
          <a class="button button-gallery en" href="??" target="blank">Gallery</a>
          <a class="button button-github en" href="https://github.com/we-are-dodo" target="blank">Github</a>
        </div>
      </div>
    </div>

    <div class="history en">
        
      <div class="subject" v-for="meet in meets" :key="meet.date">

        <div class="event-title">
          {{ meet.date }}
        </div>

        <div class="user-work-list">

          <div class="content">
            <div v-html="meet.contents"></div>
          </div>

          <div v-for="user in meet.users" :key="user.id">
            <div class="user-name">
              {{ user.name }}
            </div>
            
            <div v-for="work in user.works" :key="work">
              <div class="user-work">
                {{ work }}
              </div>
            </div>
          </div>

        </div>
      </div>
    </div>
  </div>
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
