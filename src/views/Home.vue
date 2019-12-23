<template>
  <div>
    <h2>2019景天计划</h2>
    <input type="text" v-model="tode">
    <button @click="hendle">大胆发挥</button>
    <h3>未实现</h3>
    <ul>
      <li v-for="(item,index) in list" :key="index" v-if="!item.iffalse">
        <input type="checkbox" v-model="item.iffalse" @change="change">
        {{item.title }}----------
        <button @click="removelist(index)">删除</button>
      </li>
    </ul>
    <h3>已经实现了</h3>
    <ul>
      <li v-for="(item,index) in list" :key="index" v-if="item.iffalse">
        <input type="checkbox" v-model="item.iffalse" @change="change">
        {{item.title }}----------
        <button @click="removelist(index)">删除</button>
      </li>
    </ul>
  </div>
</template>

<script>

  export default {
    name: 'home',
    data(){
      return{
        tode:'',
        list:[
          {
            title: '月入百万',
            iffalse :false,

          }
        ],

      }
    },
    methods:{
      hendle(){

        if(this.tode != ''){

          // this.list.push(this.tode)
          this.list.push({
            title:this.tode,
            isfalse:false,
          })
          this.tode = ''
        }
        console.log(this.list)
        console.log(JSON.stringify(this.list))
        localStorage.setItem('abc',JSON.stringify(this.list))
      },
      removelist(index){
        this.list.splice(index,1)
      },
      change(){
        localStorage.setItem('abc',JSON.stringify(this.list))
      }

    },
    mounted() {
    let list = JSON.parse(localStorage.getItem('abc')) ;
      console.log(list)
      this.list = list
    }
  }
</script>
