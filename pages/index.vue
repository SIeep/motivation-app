<template>
  <div class="container">
    <div>
      <h1 class="title">
        <Clock />
      </h1>
      <h2 class="subtitle">
      <Messages />
      </h2>
      <section>

        <!-- <li v-for="(message, key) in messages" :key="key">
          <ul>{{message.text}}</ul>
        </li> -->

        <!-- <p v-for="(message, key) in messages" :key="key">{{message.text}}</p> -->
        
        <!-- <button class="button is-primary is-medium"
            @click="isCardModalActive = true">
            Launch card modal (keep scroll)
        </button> -->

    </section>
    </div>
  </div>
</template>

<script>
import Clock from '~/components/Clock'
import Messages from '~/components/Messages'
import NavBar from '~/components/Header/NavBar/NavBar'
import {db} from '../plugins/firebase'

export default {
  components: {
    Clock,
    Messages,
    NavBar
  },
  created() {
    
  },
  firestore() {
    return {
      messages: db.collection("messages")
    }
  },
  data() {
    return {
      datenow: '',
      messages: ''
    }
  },
  methods: {
    time() {
      this.datenow = moment().format('h:mm:ss a')

    },
  },
  mounted() {
    this.interval = setInterval(this.time, 1000)
  },
   beforeDestroy() {
    clearInterval(this.interval)
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
