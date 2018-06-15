<template>
  <section class="container">

    <template>
      <div class="header en">
        
        <div class="logo"></div>

        <div class="label-top">
          Until next DODO
        </div>

        <div class="d-day-container">
          <div class="d-day" v-if="dday !== null">D-{{ dday }}</div>
          <div class="d-day" v-else-if="dday === 0">D-{{ dday }}</div>
          <div class="d-day" v-else>지.남</div>
        </div>

        <div class="title">
          DO <span class="span">What you want to</span> DO
        </div>

        <!-- 미디어 링크들 -->
        <div class="media-container">
          <a href="https://www.slack.com" target="blank">
            <div class="box slack">
              <div class="text">Slack</div>
            </div>
          </a>

          <a href="https://www.slack.com" target="blank">
            <div class="box facebook">
              <div class="text">Group</div>
            </div>
          </a>

          <a href="https://github.com/we-are-dodo" target="blank">
            <div class="box github">
              <div class="text">Github</div>
            </div>
          </a>
        </div>
        <!--  -->

      </div>
    </template>

    <!--  -->

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
