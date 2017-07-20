<template>
  <footer class="footer">
    <nav class="footer-item-list">
      <ul>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
      </ul>
      <span>&copy; 2017 Chany</span>
    </nav>
  </footer>
</template>
<script>
export default {
  name: "",
  data: function data() {
    return {

    }
  }
}
</script>
<style lang="sass">
.footer
  position: absolute
  bottom: 0
  width: 100%
  height: 2.5em
  line-height: 2.5em
  padding: 0 2em
  background-color: #722F21
  color: #fff

.footer-item-list
  display: flex
  align-items: center
  justify-content: center
</style>
