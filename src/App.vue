
<template>
  <div class="container">
    <div class="row my-5">
      <div class="col-md-8 offset-2">
        <button class="btn btn-success mb-3" @click="filterUsers">Filter users</button>
        <table class="table table-bordered table-hover table-striped">
          <thead>
            <tr>
              <th>T/R</th>
              <th>Name</th>
              <th>Age</th>
              <th>Address</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="item in users" :key="item.id">
              <td>{{ item.id }}</td>
              <td>{{ item.name }}</td>
              <td>{{ item.age }}</td>
              <td>{{ item.address }}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
    <div class="row my-5">
      <div class="col-md-8 offset-2">
        <h3 class="mt-3">{{ number }} metr</h3>
        <button class="btn btn-primary" @click="countNum">Yurish</button>
        <h2 class="mb-3">Qadam kattaligi {{ metr }} metr</h2>
        <button class="btn btn-secondary" @click="countMetr">Qadamni kengaytirish</button>
      </div>
    </div>
    <div class="row my-5">
      <div class="col-md-8 offset-2 mt-5">
        <button class="btn btn-success" @click="addCounter">Add counter</button>
        <div class="my-3" v-for="(item, index) in counters" :key="index">
          <button className='btn btn-success m-2' @click="increaseNum(index)">+</button>
          <span>{{item.count}}</span>
          <button className='btn btn-danger m-2' @click="decreaseNum(index)">-</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>

import { ref } from 'vue';
const users = ref([
  { id: 1, name: "Dilmurod", age: 15, address: "Olmazor" },
  { id: 2, name: "Abdulloh", age: 16, address: "Yakkatut" },
  { id: 3, name: "Doniyor", age: 17, address: "Chilonzor" },
  { id: 4, name: "Husan", age: 18, address: "Mirzo Ulug'bek" },
  { id: 5, name: "Hasan", age: 19, address: "Novza" },
  { id: 6, name: "Sherzod", age: 21, address: "Hamza" },
])
const number = ref(1)
const metr = ref(1)
const counters = ref([])

const filterUsers = () => {
  users.value.filter(item => {
    if (item.age < 18) {
      users.value.splice(item, 3)
    }
  })
}

const countMetr = () => {
  metr.value += 1
}

const countNum = () => {
  number.value = number.value + metr.value
}

const addCounter = () => {
  let obj = {count: 0}
  let newArr = [...counters.value, obj]
  counters.value = newArr
}

const increaseNum = (index) => {
  counters.value[index].count += 1
  let newArr = [...counters.value]
  counters.value = newArr
}

const decreaseNum = (index) => {
  counters.value[index].count -= 1
  let newArr = [...counters.value]
  counters.value = newArrgit 
}

</script>

<style scoped></style>