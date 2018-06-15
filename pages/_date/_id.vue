<template>
  <div v-html="body"></div>
</template>
<script>

const meets = require("~/assets/json/meets.json").meets

export default {
  data() {
    const date = this.$route.params.date
    const id = this.$route.params.id
    const meet = meets.find(meet => meet.date === date)
    if (meet) {
      const user = meet.users.find(user => user.id === id)
      if (user && user.body) {
        return {
          ...user,
        }
      }
    }
    throw {
      statusCode: 404,
      message: "Page Not Found"
    }
  },
}
</script>
