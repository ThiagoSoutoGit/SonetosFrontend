<template>
  <v-container>
    <v-btn
      text
      @click="drawer = !drawer"
    >
<!--      <v-icon v-if="drawer">mdi-arrow-right-thick</v-icon>-->
<!--      <v-icon v-else>mdi-arrow-left-thick</v-icon>-->
      <v-icon >mdi-arrow-left-thick</v-icon>
      Sonetos
    </v-btn>
    <v-navigation-drawer
        app
        clipped
        v-model="drawer"
    >
      <v-list>
        <v-list-item v-for="sonnet in sonnets" :key="sonnet.id">
          <v-btn
              text
              @click="sonnetid(sonnet.id)"
          >
            {{ sonnet.title }}
          </v-btn>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
      <v-card
          class="mx-auto my-12"
          max-width="400"
          min-width="374"
      >
        <template slot="progress">
          <v-progress-linear
              color="deep-purple"
              height="10"
              indeterminate
          ></v-progress-linear>
        </template>
        <v-card-title>{{ sonnets[currentSonnet].title }}</v-card-title>
        <v-card-text>
          <div v-html="sonnets[currentSonnet].body"></div>
        </v-card-text>
        <v-card-actions>
          <v-row justify="end">
            <v-btn
                color="primary"
                text
                @click="like()"
            >
              <v-icon justify='end'>mdi-thumb-up</v-icon><span>{{ sonnets[currentSonnet].votes }}</span>
            </v-btn>
          </v-row>
          <br>
        </v-card-actions>
<!--        <v-divider></v-divider>-->

      </v-card>
  <!--    <h5 align="left">Comments:</h5>-->
      <v-form
          ref="form"
          v-model="valid"
          lazy-validation
      >
        <v-text-field
            v-model="comment"
            label="Comente aqui"
            required
        ></v-text-field>
        <v-row justify='end'>
          <v-btn
              color="primary"
              class="mr-4"
              @click="postcomment()"
          >
            Comente
          </v-btn>
        </v-row>
      </v-form>
    <div v-for="comment in comments" :key="comment.id">
      <div v-if="comment.sonnet == sonnets[currentSonnet].id">
        <v-list-item>
          <v-list-item-avatar>
            <img src="https://cdn.vuetifyjs.com/images/john.jpg"
                 alt="john"
            >
            <!--                <img :src="comment.avatar">-->
          </v-list-item-avatar>
          <v-list-item-content style="text-align: left">
            <v-list-item-title v-html="comment.comment"></v-list-item-title>
            <v-list-item-subtitle v-html="comment.commenter"></v-list-item-subtitle>
          </v-list-item-content>
          <!--              </v-list-item>-->
          <!--              {{comment.comment}}-->
        </v-list-item>
<!--        <v-divider class="mx-4"></v-divider>-->

      </div>
    </div>
  </v-container>


</template>

<script>

import axios from "axios";
export default {
  name: 'HelloWorld',
  data () {
    return {
      sonnets: null,
      comments: null,
      currentSonnet: 0,
      drawer: null,
      comment: null,
    }
  },
  mounted () {
    let one = 'http://127.0.0.1:8000/api/sonnets?format=json'
    let two = 'http://127.0.0.1:8000/api/comments?format=json'
    const requestOne = axios.get(one)
    const requestTwo = axios.get(two)
    axios
        .all([requestOne, requestTwo])
        .then(
            axios.spread((...responses) => {
              const responseOne = responses[0];
              const responseTwo = responses[1];
              this.sonnets = responseOne.data
              this.comments = responseTwo.data
            })
        )
  },
  methods: {
    sonnetid: function (id) {
      this.currentSonnet = id - 1
    },
    like: function () {
      let sonnetnumber = this.currentSonnet + 1

      let address = 'http://127.0.0.1:8000/api/sonnets/'+sonnetnumber+'/vote';
      axios.post(address)
    },
    postcomment: function () {
      let sonnetnumber = this.currentSonnet + 1

      let address = 'http://127.0.0.1:8000/api/sonnets/'+sonnetnumber+'/vote';
      axios.post(address)
    },
    // axios.post('https:sample-endpoint.com/user', {
    //   Name: 'Fred',
    //   Age: '23'
    // })
  }
}
</script>










