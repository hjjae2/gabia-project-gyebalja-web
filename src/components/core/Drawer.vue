<!--
 * Author : 정태균
 * Part : All
-->

<template>
  <v-navigation-drawer
    id="app-drawer"
    v-model="inputValue"
    app
    dark
    floating
    persistent
    mobile-break-point="991"
    width="260"
  >
    <v-img
      :src="image"
      height="100%"
    >
      <v-layout
        class="fill-height"
        tag="v-list"
        column
      >
        <v-list-tile avatar>
          <v-list-tile-avatar
            color="white"
          >
            <v-img
              :src="logo"
              height="34"
              contain
            />
          </v-list-tile-avatar>
          <v-list-tile-title class="title">
            gㅖ발자
          </v-list-tile-title>
        </v-list-tile>
        <v-divider/>
        <v-list-tile
          v-for="(link, i) in links"
          :key="i"
          :to="link.to"
          :active-class="link.color"
          avatar
          class="v-list-item"
        >
          <v-list-tile-action>
            <v-icon>{{ link.icon }}</v-icon>
          </v-list-tile-action>
          <v-list-tile-title
            v-text="link.text"
          />
        </v-list-tile>
      </v-layout>
    </v-img>
  </v-navigation-drawer>
</template>

<script>
// Utilities
import {
  mapMutations,
  mapState
} from 'vuex'

export default {
  props: {
    opened: {
      type: Boolean,
      default: false
    }
  },

  data: () => ({
    logo: 'favicon.ico',
    links: [
      {
        to: '/',
        icon: 'mdi-view-dashboard',
        text: '메인',
        color: 'blue'
      },
      {
        to: '/boardList',
        icon: 'mdi-clipboard-outline',
        text: '게시판',
        color: 'green'
      },
      {
        to: '/myEducation',
        icon: 'mdi-book-open-page-variant',
        text: '나의 교육관리',
        color: 'info'
      },
      {
        to: '/departmentManagement',
        icon: 'mdi-finance',
        text: '부서별 랭킹',
        color: 'purple'
      },
      {
        to: '/userProfile',
        icon: 'mdi-account',
        text: '내 정보 관리',
        color: 'orange'
      }
    ]
  }),

  computed: {
    ...mapState('app', ['image', 'color']),
    inputValue: {
      get () {
        return this.$store.state.app.drawer
      },
      set (val) {
        this.setDrawer(val)
      }
    },
    items () {
      return this.$t('Layout.View.items')
    }
  },

  methods: {
    ...mapMutations('app', ['setDrawer', 'toggleDrawer'])
  }
}
</script>

<style lang="scss">
  #app-drawer {
    .v-list__tile {
      border-radius: 4px;

      &--buy {
        margin-top: auto;
        margin-bottom: 17px;
      }
    }
  }
</style>
