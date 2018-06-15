<template>
  <div>
    Hello World:-)
  </div>
</template>
<script>

const URL_PREFIX = "https://github.com/we-are-dodo/works/blob/master"
export default {
  async asyncData({app, route, error}) {
    const date = route.params.date
    const user = route.params.user
    try {
      const response = await app.$axios.get(`${URL_PREFIX}/${date}/${user}.md`)
      console.log(response.data.body)
      return {
        // asdflkasdlfkn
      }
    } catch (err) {
      if (err.response.status === 404) {
        return error({
          statusCode: 404,
          message: "Page Not Found"
        })
      }
      return error({
        statusCode: 500,
        message: "Internal Server",
      })
    }
  },
  mounted() {
    alert(this.$route.params.date)
    alert(this.user)
  }
}
</script>
