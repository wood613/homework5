<template>
  <div id="app">
    <h1 id="title" > 鮭魚價格查詢 </h1>
    <form v-on:submit.prevent="addItem">
      <p>日期:<input type="text" required v-model="itemData"></p>
      <p>商品:<input type="text" v-model="itemProduct"></p>
      <p>價格:<input type="text" v-model="itemPrice"></p>
      <button type="submit">Submit</button>
    </form>

    <table>
      <thead>
        <tr>
          <th>日期</th>
          <th>商品</th>
          <th>價格</th>
        </tr>
      </thead>
      <tbody id="table">
      <tr v-for="item in table">
        <td>{{item.day}}</td>
        <td>{{item.name}}</td>
        <td>{{item.price}}</td>
      </tr>
      </tbody>
    </table>

  </div>

</template>

<script>
export default {
  data() {
    return {
      itemData: null,
      itemProduct: null,
      itemPrice:null,
      table: [
        {day:'4/9', name: '鮭魚', price: '99' }
      ]
    }
  },
  methods: {
    addItem() {
      let item = {
        day: this.itemData,
        name: this.itemProduct,
        price: this.itemPrice
      }
      this.table.push(item);
      // 雙向綁定 HTML 內容也被清空
      this.itemData = null;
      this.itemProduct = null;
      this.itemPrice = null;

    }
  }
}
</script>

<style scoped>
body {
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 0;
}

h1 {
  text-align: center;
}

table {
  border-collapse: collapse;
  width: 100%;
}

table, th, td {
  border: 1px solid black;
}

th, td {
  padding: 10px;
  text-align: center;
}

form {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin-bottom: 20px;
}

label {
  margin-bottom: 5px;
  font-weight: bold;
}

input[type="text"] {
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
  margin-bottom: 10px;
  width: 200px;
}

button[type="submit"] {
  padding: 10px 20px;
  background-color: #4CAF50;
  color: white;
  border: none;
  border-radius: 20px;
  cursor: pointer;
}

button[type="submit"]:hover {
  background-color: #45a049;
}

#log {
  text-align: center;
  margin-bottom: 20px;
}
ul#table {
  margin-top: 20px;
  padding: 0;
  list-style-type: none;
}

ul#table li {
  margin-bottom: 5px;
}
</style>