<!--
 - Author : 정태균
 - Part : All
-->

<template>
  <div v-if="isGetData">
    <v-container
      fill-height
      fluid
      grid-list-xl>
      <v-layout
        justify-center
        wrap
      >
        <!-- 카드 -->
        <v-flex
          xs12
          md8
        >
          <material-card
            color="orange"
            title="내 정보 상세"
            text="Your profile"
            class="text-xs-center"
          >
            <v-flex
              sm12
              xs12
              md12
              lg12
            >
              <material-card
                class="v-card-profile"
              >
                <v-avatar
                  slot="offset"
                  class="mx-auto d-block"
                  size="200"
                >
                  <!-- 프로필 사진 -->
                  <img
                    :src="userImgs"
                  >
                </v-avatar>
                <!-- 직책, 부서명, 이름, 영어이름 -->
                <v-card-text class="text-xs-center">
                  <h4 class="category text-gray font-weight-thin mb-3">{{ this.$store.state.user.positionName }} / {{ this.$store.state.user.department.name }}</h4>
                  <h3 class="card-title font-weight-light"><v-icon color="black">mdi-account</v-icon>{{ this.$store.state.user.name }}<div v-if="this.$store.state.user.engName.length != 0">({{ this.$store.state.user.engName }})</div></h3>
                </v-card-text>
                <v-layout wrap>
                  <!-- 이메일 -->
                  <v-flex
                    sm12
                    xs12
                    md12
                    lg6
                  >
                    <v-card
                      class="mx-auto font-weight-bold"
                      min-height="110px"
                      hover
                    >
                      <v-card-text>
                        <h6 class="grey--text font-italic text-xs-left"><v-icon color="grey">mdi-email</v-icon>이메일(ID)</h6>
                        <div>{{ this.$store.state.user.email }}</div>
                      </v-card-text>
                    </v-card>
                  </v-flex>
                  <!-- 성별 -->
                  <v-flex
                    sm12
                    xs12
                    md12
                    lg3
                  >
                    <v-card
                      class="mx-auto  text-xs-center"
                      min-height="110px"
                      hover
                    >
                      <v-card-text>
                        <h6 class="grey--text font-italic text-xs-left"><v-icon color="grey">mdi-gender-male-female</v-icon>성별(Gender)</h6>
                        <div>{{ this.$store.state.user.gender }}</div>
                      </v-card-text>
                    </v-card>
                  </v-flex>
                  <!-- 등록번호 -->
                  <v-flex
                    sm12
                    xs12
                    md12
                    lg3
                  >
                    <v-card
                      class="mx-auto text-xs-center"
                      min-height="110px"
                      hover
                      dark
                    >
                      <v-card-text>
                        <h6 class="grey--text font-italic text-xs-left"><v-icon color="grey">mdi-shield</v-icon>등록번호</h6>
                        <div>No.{{ this.$store.state.user.id }}</div>
                      </v-card-text>
                    </v-card>
                  </v-flex>
                  <!-- 핸드폰 -->
                  <v-flex
                    sm12
                    xs12
                    md12
                    lg6
                  >
                    <v-card
                      class="mx-auto"
                      min-height="110px"
                      hover
                    >
                      <v-card-text>
                        <div>
                          <h6 class="grey--text font-italic text-xs-left"><v-icon color="grey">mdi-phone</v-icon>핸드폰 번호(Phone Number)</h6>
                          {{ this.$store.state.user.phone }}
                        </div>
                      </v-card-text>
                    </v-card>
                  </v-flex>
                  <!-- 내선 번호 -->
                  <v-flex
                    sm12
                    xs12
                    md12
                    lg6
                  >
                    <v-card
                      class="mx-auto"
                      min-height="110px"
                      hover
                    >
                      <v-card-text>
                        <h6 class="grey--text font-italic text-xs-left"><v-icon color="grey">mdi-phone-classic</v-icon>내선 번호(Tel.)</h6>
                        <div>
                          {{ this.$store.state.user.tel }}
                        </div>
                      </v-card-text>
                    </v-card>
                  </v-flex>
                </v-layout>
              </material-card>
            </v-flex>
            <!-- 버튼 -->
            <v-flex
              xs12
              text-xs-right
            >
              <router-link
                :to="{name: 'Profile Edit'}">
                <v-btn
                  class="mx-1 font-weight-light white--text"
                  color="teal"
                >
                  <v-icon color="white">mdi-pen</v-icon>
                  수정
                </v-btn>
              </router-link>
              <v-btn
                class="mx-1 font-weight-light"
                color="info"
                @click="home"
              >
                <v-icon>mdi-home</v-icon>
                홈으로
              </v-btn>
            </v-flex>
          </material-card>
        </v-flex>
      </v-layout>
    </v-container>
  </div>
</template>

<script>
export default {
  data () {
    return {
      userImgs: null,
      isGetData: false
    }
  },

  async created () {
    this.userImgs = this.$store.state.user.profileImg
    this.isGetData = true
  },
  methods: {
    home () {
      this.$router.push('/')
    }
  }
}
</script>
