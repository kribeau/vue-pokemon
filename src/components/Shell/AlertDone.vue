<template>
  <b-notification has-icon v-if="isDone" v-on="$listeners" type="is-success">
    <p>恭喜, 完成挑战!</p>
    <p>感谢使用</p>
  </b-notification>
</template>

<script>
import { mapGetters } from 'vuex'

export default {
  name: 'AlertDone',
  computed: {
    ...mapGetters(['isDone'])
  }
}
</script>
