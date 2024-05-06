<template>
  <carousel :slides="slides" :interval="3000" controls indicators @selectedDateChange="handleSelectedDateChange"></carousel>
  <div class="additional-content">
    <h2>É indeed uma pergunta</h2>
    <p v-if="selectedDate === null">Nenhuma data selecionada</p>
    <p v-else> {{ selectedDate }}</p>
  </div>
</template>

<script>
import Carousel from "./components/carousel/Carousel.vue";

export default {
  name: "App",
  components: { Carousel },
  data: () => ({
    slides: [
      {
        title: "Pergunta?",
        description: "tricky"
      },
      {},
      {},
      {
        image: "challenge.png",
      },
    ],
    selectedDate: null
  }),
  methods: {
    handleSelectedDateChange(date) {
      this.selectedDate = date;
    }
  }
};
</script>

<style scoped>
.additional-content {
    margin-top: -80px;
}
</style>
