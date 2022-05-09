<script>
export default{
  data() {
    return {
      header: 'Shopping List App',
      newItem: '',
      newItemHighPriority: false,
      items: [
        {id:1, label:'10 party hats'},
        {id:2, label:'2 board games'},
        {id:3, label:'20 cups'},
      ]
    }
  },
  methods:{
    saveItem(){
      this.items.push({id:this.items.length + 1, label: this.newItem})
      this.newItem = ""
    }
  }
}
</script>

<template>
  <div class="shopping-list">
    <h1>{{header || 'Welcome'}}</h1>
    <div class="add-item-form">
      <input
        class="add" 
        type="text" 
        @keyup.enter="saveItem"
        v-model="newItem"
        placeholder="Add an Item">
      <label>
        <input class="check" type="checkbox" v-model="newItemHighPriority">
        High Priority
      </label>
      <button
        @click="saveItem"
        class="btn">
        Save item
      </button>
    </div>
    <ul>
      <li v-for="item in items" :key="item.id">{{item.label}}</li>
    </ul>
  </div>
</template>

<style>
@import './assets/base.css';
body{
  background-color: #eaf8ff;
}
h1{
  font-size:26px;
  font-weight: bold;
  color:rgb(3, 28, 74);
}
.shopping-list{
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-49%, -49%);
  background-color: #fff;
  width: 800px;
  padding: 100px;
}
.add-item-form{
  padding:20px 0px;
}
.add{
  width: 350px;
  border:1px solid #ccc;
  outline: none;
  border-radius: 5px;
  height: 30px;
}
ul li {
  line-height: 25px;
  list-style: none;
  font-size: 18px;
}
.btn{
  width:80px;
  border: none;
  color:#fff;
  background-color: rgb(2, 103, 255);
  cursor: pointer;
  border-radius:3px;
  height: 30px;
}
</style>
