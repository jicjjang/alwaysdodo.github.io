<template>
  <li class="work" v-if="work">
    <a v-if="userBody" :href="'https://github.com/alwaysdodo/works/blob/master/' + meetDate + '/' + userId + '.md'" target="_blank">{{ work }}</a>
    <template v-else>{{ work }}</template>
  </li>
</template>

<script>
export default {
  props: {
    work: string,
    meetDate: string,
    userId: string,
    userBody: string,
  },
}
</script>

