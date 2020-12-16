<template>
  <div class="card" style="width: 25rem; background-color: beige">
    <div class="card-body">
      <h1 class="card-title">Simple To-Do</h1>
      <input type="text" v-model="yazi" />
      <p>{{ yazi }}</p>
      <button class="btn btn-primary" @click="reverseText" style="margin: 5px">
        Reverse Text
      </button>
      <button class="btn btn-success" @click="addText" style="margin: 15px">
        Ekle
      </button>
      <button class="btn btn-danger" :class="disable" @click="deleteAll">Hepsini Sil</button>
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
</template>

<script>
export default {
  data() {
    return {
      yazi: "",
      yeni: [],
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
    reverseText() {
      this.yazi = this.yazi
        .split("")
        .reverse()
        .join("");
    },
    addText() {
      if (this.yazi) {
        this.yeni.push(this.yazi);
        this.clear();
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
    clear() {
      this.yazi = "";
    },
  },
  computed: {
    disable() {
      return {
        "disabled" : this.yeni === "",
      };
    },
  },
};
</script>

<style scoped></style>
