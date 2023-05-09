<template>
  <q-page class="relative-position">
    <q-scroll-area class="absolute fullscreen">
      <div class="q-py-lg q-px-md row items-end q-col-gutter-md">
        <div class="col">
          <q-input 
            v-model="novoConteudoTweet" 
            class="novo-tweet" 
            placeholder="O que está acontecendo?" 
            counter 
            autogrow
            maxlength="280">
            <template v-slot:before>
              <q-avatar size="xl">
                <img src="https://pbs.twimg.com/profile_images/1528093885704052741/j0bYT17V_400x400.jpg">
              </q-avatar>
            </template>
          </q-input>
        </div>
        <div class="col col-shrink">
          <q-btn 
            @click="addNovoTweet" 
            :disable="!novoConteudoTweet" 
            unelevated 
            rounded 
            no-caps 
            color="light-blue"
            label="Tweetar" 
            text-color="white" 
            class="q-mb-lg" 
          />
        </div>
      </div>
      <q-separator color="grey-4" />

      <q-list separator>
        <transition-group appear enter-active-class="animated fadeIn slow" leave-active-class="animated fadeOut slow">
          <q-item v-for="tweet in tweets" :key="tweet.date" class="q-py-md tweet">

            <q-item-section avatar top>
              <q-avatar size="xl">
                <img src="https://pbs.twimg.com/profile_images/1528093885704052741/j0bYT17V_400x400.jpg">
              </q-avatar>
            </q-item-section>

            <q-item-section>
              <q-item-label class="text-subtitle1">
                <strong>{{ username }}</strong>
                <span class="text-grey-7">
                  {{ user }}
                  <br class="lt-md"> &bull;
                  {{ dataRelativa(tweet.date) }}
                </span>

              </q-item-label>
              <q-item-label class="conteudo-tweet text-body1">
                {{ tweet.content }}
              </q-item-label>
              <div class="icones-tweet row justify-between q-mt-sm">
                <q-btn 
                  flat 
                  round 
                  color="grey" 
                  size="sm" 
                  icon="far fa-comment" 
                />
                <q-btn 
                  flat 
                  round 
                  color="grey" 
                  size="sm" 
                  icon="fas fa-retweet" 
                />
                <q-btn 
                  flat 
                  round 
                  color="grey" 
                  size="sm" 
                  icon="far fa-heart" 
                />
                <q-btn 
                  @click="deletaTweet(tweet)" 
                  flat 
                  round 
                  color="grey" 
                  size="sm" 
                  icon="fas fa-trash" 
                />
              </div>
            </q-item-section>


          </q-item>
        </transition-group>
      </q-list>

    </q-scroll-area>

  </q-page>
</template>

<script>
import { formatDistance } from 'date-fns'

export default ({
  name: 'PageHome',
  data() {
    return {
      username: 'Cadu Maverick',
      user: ' @cadumaverick',
      novoConteudoTweet: '',
      tweets: [
        {
          content: 'peixe peixe peixe',
          date: 1682972239365
        },
        {
          content: 'cadu sou eu cara',
          date: 1682859098760
        },
        {
          content: 'como usa isso aqui',
          date: 1682637752898
        },
        {
          content: 'hahahaha',
          date: 1682536256190
        },
        {
          content: 'testando',
          date: 1682299588461
        },
        {
          content: 'oi!',
          date: 1682299617605
        },

      ],
    }
  },
  methods: {
    addNovoTweet() {
      let novoTweet = {
        content: this.novoConteudoTweet,
        date: Date.now()
      }
      this.tweets.unshift(novoTweet)
      this.novoConteudoTweet = ''
    },
    deletaTweet(tweet) {
      let dataPraDeletar = tweet.date
      let index = this.tweets.findIndex(tweet => tweet.date === dataPraDeletar)
      this.tweets.splice(index, 1)
    },
    dataRelativa(value) {
      return formatDistance(value, new Date())
    }
  }
})
</script>

<style>
.novo-tweet textarea {
  font-size: 19px;
  line-height: 1.4 !important;
}

.icones-tweet {
  margin-left: -5px;
}

.tweet:not(:first-child) {
  border-top: 1px solid rgba(0, 0, 0, 0.12)
}

.tweet {
  word-break: break-word;
}
</style>