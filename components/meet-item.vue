<template>
  <div class="meet">
    <div class="header" @click="isOpened = !isOpened">
      <span class="title en">{{ meet.date }}</span>
      <span class="icon icon-close">&times;</span>
    </div>
    <div class="body" v-if="isOpened">
      <div class="intro" v-html="meet.contents"></div>
      <div class="users">
        <div class="user" v-for="user in meet.users" :key="user.id">
          <div class="name">{{ user.name }}</div>
          <ul class="works">
            <li class="work" v-for="work in user.works" :key="work">
              <nuxt-link v-if="user.body" :to="'/' + meet.date + '/' + user.id">{{ work }}</nuxt-link>
              <template v-else>{{ work }}</template>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    meet: null,
    opened: Boolean,
  },
  data() {
    return {
      isOpened: this.opened,
    }
  },
}
</script>
