<template>
  <div>
    <h1>Flask API Test</h1>
    <button @click="fetchHello">GET /hello</button>
    <button @click="sendData">POST /echo</button>
    <p>{{ response }}</p>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      response: "",
    };
  },
  methods: {
    // GETリクエスト
    async fetchHello() {
      try {
        const res = await axios.get("http://127.0.0.1:5000/api/hello");
        this.response = res.data.message;
      } catch (error) {
        console.error("Error fetching hello:", error);
      }
    },
    // POSTリクエスト
    async sendData() {
      try {
        const payload = { name: "Vue User", age: 25 };
        const res = await axios.post("http://127.0.0.1:5000/api/echo", payload);
        this.response = res.data;
      } catch (error) {
        console.error("Error sending data:", error);
      }
    },
  },
};
</script>