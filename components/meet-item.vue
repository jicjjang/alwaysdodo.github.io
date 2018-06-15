<template>
  <div class="meet" :class="{toggle: isOpened}">
    <div class="header" @click="isOpened = !isOpened">
      <span class="title en">{{ meet.date }}</span>
      <span class="icon icon-close"></span>
    </div>
    <transition name="toggle">
      <div class="body" v-if="isOpened">
        <div class="intro" v-html="meet.contents"></div>
        <div class="users">
          <div class="user" v-for="user in meet.users" :key="user.id">
            <div class="name">{{ user.name }}</div>
            <ul class="works">
              <li class="work" v-for="work in user.works" :key="work">
                <a v-if="user.body" :href="'https://github.com/we-are-dodo/works/blob/master/' + meet.date + '/' + user.id + '.md'" target="_blank">{{ work }}</a>
                <template v-else>{{ work }}</template>
              </li>
            </ul>
          </div>
        </div>
      </div>
    </transition>
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
