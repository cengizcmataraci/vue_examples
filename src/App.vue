<template>
  <div>
    <div id="practice" class="col d-flex justify-content-center ust">
      <div class="card" style="width: 25rem; background-color: beige">
        <div class="card-body">
          <h1 class="card-title">Simple To-Do</h1>
          <input type="text" v-model="yazi" />
          <p>{{ yazi }}</p>
          <button
            class="btn btn-primary"
            @click="reverseText"
            style="margin: 5px"
          >
            Reverse Text
          </button>
          <button class="btn btn-success" @click="addText" style="margin: 15px">
            Ekle
          </button>
          <button class="btn btn-danger" @click="deleteAll">Hepsini Sil</button>
        </div>
        <ol>
          <li v-for="(den, index) in yeni" :key="index" class="list-item">
            <span>{{ den }}</span>
            <button
              class="btn btn-sm btn-danger"
              style="margin-left: 20px"
              @click="deleteItem(index)"
            >
              Sil
            </button>
          </li>
        </ol>
      </div>
      <div
        class="card"
        style="width: 24rem; background-color: beige; margin: 25px"
      >
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
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "practice",
  data() {
    return {
      counter: 0,
      yazi: "",
      yeni: [],
      bgc: "dangerZone",
    };
  },
  mounted() {
    if (localStorage.yeni) {
      this.yeni = JSON.parse(localStorage.yeni);
    }
  },
  watch: {
    yeni: {
      handler(newText) {
        localStorage.yeni = JSON.stringify(newText);
      },
      deep: true,
    },
  },
  methods: {
    increaseNumber() {
      this.counter++;
    },
    lowerNumber() {
      this.counter--;
    },
    reverseText() {
      this.yazi = this.yazi
        .split("")
        .reverse()
        .join("");
    },
    addText() {
      if (this.yazi) {
        this.yeni.push(this.yazi);
      } else {
        alert("Boş gönderemezsin!");
      }
    },
    deleteItem(index) {
      this.yeni.splice(index, 1);
    },
    deleteAll(index) {
      this.yeni.splice(index);
    },
  },
  computed: {},
};
</script>

<style>
.ust {
  margin-top: 150px;
  text-align: center;
  vertical-align: middle;
}
.dangertext {
  color: #f9000f;
  font-size: larger;
}
.dangerZone {
  background-color: darkred;
  color: aliceblue;
}
</style>
