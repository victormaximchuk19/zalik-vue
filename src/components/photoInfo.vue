<template>
  <div class="my-4">
    <b-card>
      <b-card-text class="text-left">
        Id: 3
      </b-card-text>
      <b-card-text class="text-left">
        Author: Василь Іванович
      </b-card-text>
      <b-card-text class="text-left">
        Name: Моє фото
      </b-card-text>
      <b-card-text class="text-left">
        Description: Фото як я навчаюсь
      </b-card-text>
      <b-card-text class="text-left">
        Tags: #study, #student
      </b-card-text>
      <b-card-text class="text-left">
        Publication date: 21.1.2021
      </b-card-text>
      <b-card-text class="text-left">
        Likes: 3
      </b-card-text>
      <hr>
      <b-card-body>
        <div class="text-center my-4">
          Comments:
        </div>
        <b-row>
          <b-col cols='12'>
            <b-input @keyup="search" placeholder='find comment...' v-model="searchValue"/>
          </b-col>
        </b-row>
        <div v-for="comment in comments">
          <b-card
            style="max-width: 100%;"
            class='mt-2'
          >
            <b-card-text class="text-left">
              Author: {{ comment.author }}
            </b-card-text>
            <b-card-text class="text-left">
              Content: {{ comment.content }}
            </b-card-text>
          </b-card>
        </div>
      </b-card-body>
    </b-card>
  </div>
</template>

<script>
export default {
  data() {
    return {
      comments: [
        { author: 'Маша', content: 'Чудово!' },
        { author: 'Віктор', content: 'Супер!' },
        { author: 'Віталій', content: ":)" },
        { author: 'Наталія', content: 'Класс!' }
      ],
      searchValue: null
    }
  },
  mounted() {
    localStorage.comments = JSON.stringify(this.comments);
  },
  methods: {
    search() {
      this.comments = JSON.parse(localStorage.comments).filter(c => c.author.toLowerCase().includes(this.searchValue.toLowerCase()));
    }
  }
}
</script>

<style scoped>
</style>
