<template>
  <nav>
    <div class="container--links">
      <ul class="list--links">
        <li class="item--link">
          <router-link to="/">DATA 1</router-link>
        </li>
        <li class="item--link">
          <router-link to="/about">DATA 2</router-link>
        </li>
        <li class="item--link">
          <router-link to="/cart">DATA 3</router-link>
        </li>
      </ul>
    </div>
  </nav>
  <div class="container--main">
    <div class="container--items">
      <div class="item" v-for="item in items" :key="item.id">
        <h2>{{ item.title }}</h2>
        <p>{{ item.body }}</p>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      items: [

      ],
    }
  },
  mounted() {
    axios.get("http://localhost:3000/items").then((res) => {
      this.items = res.data
    })
  }
}
</script>

<style>
* {
  font-family: "Calibri", sans-serif;
  margin: 0;
}

.list--links {
  display: flex;
  flex-direction: row;
}

.item--link {
  list-style: none;
}

.container--main {
  display: flex;
  justify-content: center;
  align-items: center;
}

.container--items {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  width: 912px;
  justify-content: space-around;
  padding: 20px;
}

.item {
  border: 1px solid teal;
  margin-top: 10px;
  width: 250px;
  height: 250px;
  padding: 20px;

}
</style>
