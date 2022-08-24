<template>
  <div >
      <ul>
        <li v-for="(item,index) in arr" :key="item">{{item}} <button @click="del(index)">删除</button></li>
      </ul>
        <button @click="newNum">生成</button>
  </div>
</template>

<script>


export default {
    data(){
      return {
        arr:[]
      }
    },
    methods:{
      newNum(){
        let a = Math.floor(Math.random()*20)
        while(this.arr.indexOf(a)!==-1){
          a = Math.floor(Math.random()*20)
        }
          this.arr.push(a)
      },
      del(index){
          this.arr.splice(index,1)
      }
    }
}
</script>

<style >

</style>
