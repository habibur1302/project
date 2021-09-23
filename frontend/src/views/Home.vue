<template>
  <div class="row">
    <div class="col text-center">
<!--      <img alt="Vue logo" src="../assets/logo.png">-->
      <div v-if="user">
        <h4 class="mt-5">WELCOME {{ user.name | capitalize }}</h4>
        <h4> Birth Day: {{ user.date_of_birth | dateFormate }}</h4>
      </div>
      <div v-else>
        <h4 class="mt-5">WELCOME</h4>
      </div>
<!--      <p>Laravel 6 Backend API Ready</p>-->
    </div>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'
import moment from 'moment'

export default {
  computed: mapGetters({
    user: 'auth/user'
  }),
  components: {
    //
  },
  filters: {
    capitalize: function (value) {
      return value.toUpperCase()
    },
    dateFormate: function (value) {
      return moment(String(value)).format('MMM DD, YYYY')
    }
  },

  metaInfo () {
    return { title: this.$t('home') }
  }
}
</script>
