<template>
  <topic-list :topic-list="playList" />
</template>

<script>
import { fetchTopicList } from '~/utils'
import TopicList from '~/components/TopicList'

export default {
  head () {
    return {
      titleTemplate: '%s - 好玩'
    }
  },
  components: {
    TopicList
  },
  async asyncData ({ app }) {
    const nodes = ['share', 'bb', 'games', 'travel', 'hardware']
    const playList = await fetchTopicList(app.$axios, nodes)

    return {
      playList
    }
  },
  layout: 'mobile'
}
</script>
