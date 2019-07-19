<template lang="html">
  <footer class="footer">
    <div class="has-text-centered">
      <p>
        Made with
        <b-icon color="red" type="is-success" size="is-small" icon="vuejs" />
        by
        <a href="https://github.com/kribeau" target="_blank">mumu</a>
      </p>
      
    </div>
  </footer>
</template>

<script>
export default {
  name: 'Footer',
  version: process.env.VUE_APP_VERSION
}
</script>

<style lang="scss">
.footer {
  background-color: transparent !important;
  font-family: monospace;
  a {
    color: #000;
  }
}
</style>
