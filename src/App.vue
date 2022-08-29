<template>
  <div id="app">
    <div class="container">
      <div class="title">
        <h1>1 le 100 arasında bir sayı tutacağım , tahmin et</h1>
      </div>

      <div class="input">
        <p>Tuttum Tahmin Et</p>
        <input
          v-model="b"
          id="girdi"
          placeholder="Tahmin et"
          type="number"
          min="1"
          max="100"
        />
      </div>
      <div class="submit">
        <button @click="fonksiyon">Onayla</button>
      </div>

      <div id="result">{{ result }}</div>
      <br />
      <div class="attempt">Tüm Denemelerin ={{ denemeler }}</div>
      <br />
      <div v-if="show" class="numbofattempts">
        {{ numbOfAttempts }} Denemede Bildin
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  components: {},
  data: function () {
    return {
      result: "",
      a: Math.floor(Math.random() * 101),
      b: document.getElementById("girdi").value,
      denemeler: [],
      numbOfAttempts: "",
      show: false,
    };
  },
  methods: {
    fonksiyon: function () {
      if (this.b > 100) {
        window.alert("100'den küçük bir değer giriniz");
      }
      if (this.a == this.b) {
        this.result = "Bildin Helal Olsun!";
        this.numbOfAttempts = this.denemeler.length;
        this.show = true;
      }
      if (this.b < this.a) {
        this.result = "Bilemedin Yukarı Çık";
      }
      if (this.b > this.a) {
        this.result = "Bilemedin Aşağı İn";
      }
      this.denemeler.push(document.getElementById("girdi").value);
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
body {
  background-color: aqua;
}

button {
  width: 200px;
  height: 50px;
  border-radius: 10px;
  cursor: pointer;
  font-size: large;
  text-align: center;
  background-color: antiquewhite;
  color: red;
}
.input {
  margin-top: 50px;
}
#girdi {
  width: 100px;
  height: 25px;
}
.submit {
  margin-top: 40px;
}
</style>
