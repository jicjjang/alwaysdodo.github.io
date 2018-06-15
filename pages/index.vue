<template>
  <section class="container">

    <!-- 제일위 로고 -->

    <template>
      <div class="header">
        
        <div class="logo"></div>

        <div class="label-top">
          Until next DODO
        </div>

        <div class="d-day-container">
          <div class="d-day">D-{{ dday }}</div>
        </div>

        <div class="title">
          DO <span class="span">What you want to</span> DO
        </div>

        <div class="media-container">
          <div class="box slack">
            Slack
          </div>

          <div class="box facebook">
          </div>

          <div class="box github">
          </div>
        </div>

      </div>
    </template>

    <!--  -->

    <div class="">

    </div>


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
// import AppLogo from '~/components/AppLogo.vue'


// https://github.com/we-are-dodo/works/tree/master/1970-01-01

// const LIST_URL_PREFIX = "https://github.com/we-are-dodo/works/tree/master"
// const rounds = [
//   "1970-01-01",
// ]

import * as moment from "moment"
import "moment-timezone"

const NEXT_DODO_DATE = moment.tz("2018-06-18 19:30:00", "Asia/Seoul")

export default {
  components: {
  },
  async asyncData({app}) {
    return {
      meets: [
        {
          date: "2018-03-31",
          contents: `일시  /  2018년 03월 31일(토) 19:30 ~ 04월 01일 07:30<br />
장소   /  신대방역 Dev@agit<br />
참여자   /  이대명, 김지윤, 박성일, 정경호, 조호찬, 유다정, 유성민`,
          users: [
            {
              id: "dajung",
              name: "유다정",
              works: [
                {title: "디자이너, 첫 회사 생활로 배운 6가지 업무 습관", linkable: true},
              ],
            },
            {
              id: "seongmin",
              name: "유성민",
              works: [
                {title: "하던거 계속 하면 된다고 해서 왔어", linkable: false},
              ],
            },
          ],
        }
      ],
    }
  },
  data() {
    return {
      dday: 0,
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
