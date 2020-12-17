<template>
  <div class="card" style="width: 25rem; background-color: beige; margin: 25px">
    <div class="card-body">
      <h1 class="card-title">10'u Geçme!</h1>
      <p>{{ counter }}</p>
      <button
        class="btn btn-primary"
        @click="increaseNumber"
        style="margin: 5px"
      >
        Increase
      </button>
      <button class="btn btn-danger" @click="lowerNumber">Lower</button>
      <p v-if="counter == 10">
        Şu an {{ counter }} sayısındasınız. Bu sayıyı geçmeyiniz!
      </p>
      <p v-if="counter > 10" class="dangertext" :class="bgc">
        <strong>Asla laf anlamıyorsun!</strong>
      </p>
      <p><button class="btn btn-primary" @click="myFunction">{{ postTitle }}</button></p>
    </div>
  </div>
</template>

<script>
export default {
  props: ['postTitle'],
  data() {
    return {
      counter: 0,
      bgc: "dangerZone",
    };
  },
  methods: {
    increaseNumber() {
      this.counter++;
    },
    lowerNumber() {
      this.counter--;
    },
    myFunction() {
      setTimeout(() => {
        alert(this.postTitle);
      }, 3000);
    },
  },
  computed: {

  },
};
</script>

<style scoped></style>
