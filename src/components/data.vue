<template>
  <div id="app">
    <div class="form-container">
      <form v-on:submit.prevent="addItem" class="input-form">
        <div class="input-row">
          <label for="date">日期</label>
          <input type="text" id="date" name="date" v-model="date">
        </div>
        <div class="input-row">
          <label for="name">產品名稱</label>
          <input type="text" id="name" name="name" v-model="name">
        </div>
        <div class="input-row">
          <label for="price">價格</label>
          <input type="text" id="price" name="price" v-model="price">
        </div>
        <button type="submit">Submit</button>
      </form>
    </div>

    <div class="data-container">
      <button v-on:click="toggleData">顯示資料</button>
      <table v-if="showData">
        <thead>
        <tr>
          <th>日期</th>
          <th>名稱</th>
          <th>價格</th>
        </tr>
        </thead>
        <tbody>
        <tr v-for="item in data">
          <td>{{ item.date }}</td>
          <td>{{ item.name }}</td>
          <td>{{ item.price }}</td>
        </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      date: null,
      name: null,
      price: null,
      data: [],
      showData: false
    };
  },
  methods: {
    addItem() {
      let item = {
        date: this.date,
        name: this.name,
        price: this.price
      };
      this.data.push(item);
      this.date = null;
      this.name = null;
      this.price = null;
    },
    toggleData() {
      this.showData = !this.showData;  // 切换显示状态
    }
  }
};
</script>

<style scoped>
#app {
  padding: 20px;
}

.form-container {
  display: flex;
  flex-direction: row;
}

.input-form {
  margin-right: 20px;
}

.input-row {
  display: flex;
  align-items: center;
  margin-bottom: 10px;
}

.input-row label {
  margin-right: 10px;
}

.data-container {
  margin-top: 20px;
}

table {
  border-collapse: collapse;
  width: 100%;
}

table th,
table td {
  border: 1px solid #ccc;
  padding: 8px;
  text-align: left;
}

table th {
  background-color: #f2f2f2;
  font-weight: bold;
}

button {
  padding: 10px 20px;
  background-color: rgb(128, 128, 128);
  color: white;
  border: none;
  cursor: pointer;
}
</style>
