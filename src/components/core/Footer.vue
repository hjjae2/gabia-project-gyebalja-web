<!--
 * Author : 이현재
 * Part : All
-->

<template>
  <v-footer
    id="core-footer"
    absolute
    height="82"
  >
    <div class="footer-items">
      <span
        v-for="link in links"
        :key="link.name"
      >
        <a
          :href="link.Link"
          target="_blank"
          class="tertiary--text footer-links">{{ link.name }}</a>
      </span>
    </div>
  </v-footer>
</template>

<script>
export default {
  data: () => ({
    links: [
      { name: 'Home', Link: '/#' },
      { name: 'Gabia Homepage', Link: 'https://www.gabia.com/' },
      { name: 'About Us', Link: 'https://company.gabia.com/' },
      { name: 'GITHUB', Link: 'https://github.com/gabia-intern-team-2/gabia-project-gyebalja-web' }
    ]
  })
}
</script>

<style>
#core-footer {
  z-index: 0;
}
</style>
