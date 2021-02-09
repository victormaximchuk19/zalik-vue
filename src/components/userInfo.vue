<template>
  <div class="container">
    <b-row>
      <b-col>
        <h3>
          Student #{{ studentNumber }} info
        </h3>
      </b-col>
    </b-row>
    <b-row>
      <b-col class="d-flex justify-content-center">
        <b-card
          title="Василь Іванович"
          img-src="https://i2.wp.com/rollercoasteryears.com/wp-content/uploads/Thrive-During-Finals-.jpg?resize=1000%2C667&ssl=1"
          img-alt="Image"
          img-top
          tag="article"
          style="max-width: 50rem;"
          class="my-4"
        >
          <b-card-text>
            Варіант 21
          </b-card-text>
          <b-card-text>
            Студент 4-го крусу математичного факультету
          </b-card-text>
          <b-button @click="showPhotoInfo"> {{showInfo ? 'Hide' : 'Show'}} info </b-button>
          <b-card-body>
            <photoInfo v-show="showInfo"/>
          </b-card-body>
        </b-card>
      </b-col>
    </b-row>
  </div>
</template>

<script>
import photoInfo from './photoInfo';
export default {
  components: {
    photoInfo
  },
  data() {
    return {
      studentNumber: null,
      showInfo: false
    };
  },
  mounted() {
    this.studentNumber = this.$route.params.id
  },
  methods: {
    showPhotoInfo() {
      this.showInfo = !this.showInfo;
    }
  }
}
</script>

<style scoped>

</style>
